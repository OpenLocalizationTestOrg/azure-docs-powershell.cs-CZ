---
title: "Zachování přihlášení uživatele napříč relacemi PowerShellu"
description: "Tento článek popisuje nové funkce v Azure PowerShellu, které umožňují opětovné použití přihlašovacích údajů a dalších informací o uživateli napříč několika relacemi PowerShellu."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 8ef20796b64b16c78a653e293a57d5e752d89710
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="persisting-user-logins-across-powershell-sessions"></a><span data-ttu-id="e2488-103">Zachování přihlášení uživatele napříč relacemi PowerShellu</span><span class="sxs-lookup"><span data-stu-id="e2488-103">Persisting user logins across PowerShell sessions</span></span>

<span data-ttu-id="e2488-104">Ve verzi Azure PowerShellu vydané v září 2017 zavádějí rutiny Azure Resource Manageru novou funkci **automatického ukládání kontextu Azure**.</span><span class="sxs-lookup"><span data-stu-id="e2488-104">In the September 2017 release of Azure PowerShell, Azure Resource Manager cmdlets introduce a new feature, **Azure Context Autosave**.</span></span> <span data-ttu-id="e2488-105">Tato funkce umožňuje uživatelům několik nových scénářů, včetně:</span><span class="sxs-lookup"><span data-stu-id="e2488-105">This feature enables several new user scenarios, including:</span></span>

- <span data-ttu-id="e2488-106">Uchování přihlašovacích údajů pro opětovné použití v nových relacích PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-106">Retention of login information for reuse in new PowerShell sessions.</span></span>
- <span data-ttu-id="e2488-107">Snadnější použití úloh na pozadí pro provádění dlouhotrvajících rutin.</span><span class="sxs-lookup"><span data-stu-id="e2488-107">Easier use of background tasks for executing long-running cmdlets.</span></span>
- <span data-ttu-id="e2488-108">Přepínání mezi účty, předplatnými a prostředími bez samostatného přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e2488-108">Switch between accounts, subscriptions, and environments without a separate login.</span></span>
- <span data-ttu-id="e2488-109">Současné provádění úloh s použitím různých přihlašovacích údajů a předplatných ze stejné relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-109">Execution of tasks using different credentials and subscriptions, simultaneously, from the same PowerShell session.</span></span>

## <a name="azure-contexts-defined"></a><span data-ttu-id="e2488-110">Definice kontextů Azure</span><span class="sxs-lookup"><span data-stu-id="e2488-110">Azure contexts defined</span></span>

<span data-ttu-id="e2488-111">*Kontext Azure* je soubor informací, který definuje cíl rutin Azure PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-111">An *Azure context* is a set of information that defines the target of Azure PowerShell cmdlets.</span></span> <span data-ttu-id="e2488-112">Kontext se skládá z pěti částí:</span><span class="sxs-lookup"><span data-stu-id="e2488-112">The context consists of five parts:</span></span>

- <span data-ttu-id="e2488-113">*Účet* – Uživatelské jméno nebo instanční objekt používané k ověřování komunikace s Azure.</span><span class="sxs-lookup"><span data-stu-id="e2488-113">An *Account* - the UserName or Service Principal used to authenticate communications with Azure</span></span>
- <span data-ttu-id="e2488-114">*Předplatné* – Předplatné Azure obsahující prostředky, se kterými se pracuje.</span><span class="sxs-lookup"><span data-stu-id="e2488-114">A *Subscription* - The Azure Subscription containing the Resources being acted upon.</span></span>
- <span data-ttu-id="e2488-115">*Tenant* – Tenant Azure Active Directory obsahující vaše předplatné.</span><span class="sxs-lookup"><span data-stu-id="e2488-115">A *Tenant* - The Azure Active Directory tenant that contains your subscription.</span></span> <span data-ttu-id="e2488-116">Tenanti jsou důležitější pro ověřování instančního objektu.</span><span class="sxs-lookup"><span data-stu-id="e2488-116">Tenants are more important to ServicePrincipal authentication.</span></span>
- <span data-ttu-id="e2488-117">*Prostředí* – Konkrétní cloud Azure, na který se cílí, obvykle globální cloud Azure.</span><span class="sxs-lookup"><span data-stu-id="e2488-117">An *Environment* - The particular Azure Cloud being targeted, usually the Azure global Cloud.</span></span>
  <span data-ttu-id="e2488-118">Nastavení prostředí však umožňuje cílit i na národní cloudy, cloudy pro státní správu a místní cloudy (Azure Stack).</span><span class="sxs-lookup"><span data-stu-id="e2488-118">However, the environment setting allows you to target National, Government, and on-premises (Azure Stack) clouds as well.</span></span>
- <span data-ttu-id="e2488-119">*Přihlašovací údaje* – Informace, které Azure používá k ověření vaší identity a zajištění vašeho oprávnění k přístupu k prostředkům v Azure.</span><span class="sxs-lookup"><span data-stu-id="e2488-119">*Credentials* - The information used by Azure to verify your identity and ensure your authorization to access resources in Azure</span></span>

<span data-ttu-id="e2488-120">V předchozích verzích se kontext Azure musel vytvořit při každém otevření nové relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-120">In previous releases, your Azure Context had to be created each time you opened a new PowerShell session.</span></span> <span data-ttu-id="e2488-121">Od Azure PowerShellu verze 4.4.0 můžete povolit automatické ukládání a opětovné použití kontextů Azure, kdykoli otevřete novou relaci PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-121">Beginning with Azure PowerShell v4.4.0, you can enable the automatic saving and reuse of Azure Contexts whenever you open a new PowerShell session.</span></span>

## <a name="automatically-saving-the-context-for-the-next-login"></a><span data-ttu-id="e2488-122">Automatické ukládání kontextu pro další přihlášení</span><span class="sxs-lookup"><span data-stu-id="e2488-122">Automatically saving the context for the next login</span></span>

<span data-ttu-id="e2488-123">Azure PowerShell ve výchozím nastavení zahodí informace o kontextu při zavření relace PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-123">By default, Azure PowerShell discards your context information whenever you close the PowerShell session.</span></span>

<span data-ttu-id="e2488-124">Pokud chcete povolit, aby si Azure PowerShell pamatoval kontext po zavření relace PowerShellu, použijte `Enable-AzureRmContextAutosave`.</span><span class="sxs-lookup"><span data-stu-id="e2488-124">To allow Azure PowerShell to remember your context after the PowerShell session is closed, use `Enable-AzureRmContextAutosave`.</span></span> <span data-ttu-id="e2488-125">Informace o kontextu a přihlašovacích údajích se automaticky uloží do speciální skryté složky v uživatelském adresáři (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="e2488-125">Context and credential information are automatically saved in a special hidden folder in your user directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span>
<span data-ttu-id="e2488-126">Následně bude každá nová relace PowerShellu cílit na kontext použitý v poslední relaci.</span><span class="sxs-lookup"><span data-stu-id="e2488-126">Subsequently, each new PowerShell session targets the context used in your last session.</span></span>

<span data-ttu-id="e2488-127">Pokud chcete PowerShell nastavit tak, aby kontext a přihlašovací údaje zapomínal, použijte `Disable-AzureRmContextAutoSave`.</span><span class="sxs-lookup"><span data-stu-id="e2488-127">To set PowerShell to forget your context and credentials, use `Disable-AzureRmContextAutoSave`.</span></span> <span data-ttu-id="e2488-128">Při každém otevření relace PowerShellu se budete muset přihlásit k Azure.</span><span class="sxs-lookup"><span data-stu-id="e2488-128">You will need to log in to Azure every time you open a PowerShell session.</span></span>

<span data-ttu-id="e2488-129">Rutiny umožňující správu kontextů Azure umožňují také podrobné řízení.</span><span class="sxs-lookup"><span data-stu-id="e2488-129">The cmdlets that allow you to manage Azure contexts also allow you fine grained control.</span></span> <span data-ttu-id="e2488-130">Pokud chcete, změny se můžou použít pouze pro aktuální relaci PowerShellu, (rozsah `Process`) nebo pro každou relaci PowerShellu (rozsah `CurrentUser`).</span><span class="sxs-lookup"><span data-stu-id="e2488-130">If you want changes to apply only to the current PowerShell session (`Process` scope) or every PowerShell session (`CurrentUser` scope).</span></span> <span data-ttu-id="e2488-131">Podrobnější popis těchto možností najdete v části [Používání rozsahů kontextu](#Using-Context-Scopes).</span><span class="sxs-lookup"><span data-stu-id="e2488-131">These options are discussed in mode detail in [Using Context Scopes](#Using-Context-Scopes).</span></span>

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a><span data-ttu-id="e2488-132">Spouštění rutin Azure PowerShellu jako úloh na pozadí</span><span class="sxs-lookup"><span data-stu-id="e2488-132">Running Azure PowerShell cmdlets as background jobs</span></span>

<span data-ttu-id="e2488-133">Funkce **automatického ukládání kontextu Azure** umožňuje také sdílení kontextu s úlohami PowerShellu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e2488-133">The **Azure Context Autosave** feature also allows you to share you context with PowerShell background jobs.</span></span> <span data-ttu-id="e2488-134">PowerShell umožňuje spouštět a monitorovat dlouhotrvající úlohy jako úlohy na pozadí bez nutnosti čekat na jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="e2488-134">PowerShell allows you to start and monitor long-executing tasks as background jobs without having to wait for the tasks to complete.</span></span> <span data-ttu-id="e2488-135">Přihlašovací údaje můžete s úlohami na pozadí sdílet dvěma různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="e2488-135">You can share credentials with background jobs in two different ways:</span></span>

- <span data-ttu-id="e2488-136">Předání kontextu jako argumentu</span><span class="sxs-lookup"><span data-stu-id="e2488-136">Passing the context as an argument</span></span>

  <span data-ttu-id="e2488-137">Většina rutin AzureRM umožňuje předání kontextu do rutiny v podobě parametru.</span><span class="sxs-lookup"><span data-stu-id="e2488-137">Most AzureRM cmdlets allow you to pass the context as a parameter to the cmdlet.</span></span> <span data-ttu-id="e2488-138">Kontext můžete do úlohy na pozadí předat způsobem znázorněným v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e2488-138">You can pass a context to a background job as shown in the following example:</span></span>

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- <span data-ttu-id="e2488-139">Použití výchozího kontextu s povoleným automatickým ukládáním</span><span class="sxs-lookup"><span data-stu-id="e2488-139">Using the default context with Autosave enabled</span></span>

  <span data-ttu-id="e2488-140">Pokud jste povolili **automatické ukládání kontextu**, úlohy na pozadí automaticky používají výchozí uložený kontext.</span><span class="sxs-lookup"><span data-stu-id="e2488-140">If you have enabled **Context Autosave**, background jobs automatically use the default saved context.</span></span>

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

<span data-ttu-id="e2488-141">Pokud potřebujete znát výsledek úlohy na pozadí, použijte `Get-Job` ke kontrole stavu úlohy a `Wait-Job` k čekání na dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="e2488-141">When you need to know the outcome of the background task, use `Get-Job` to check the job status and `Wait-Job` to wait for the Job to complete.</span></span> <span data-ttu-id="e2488-142">Pomocí `Receive-Job` můžete zachytit nebo zobrazit výstup úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e2488-142">Use `Receive-Job` to capture or display the output of the background job.</span></span> <span data-ttu-id="e2488-143">Další informace najdete v tématu [Informace o úlohách](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="e2488-143">For more information, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

## <a name="creating-selecting-renaming-and-removing-contexts"></a><span data-ttu-id="e2488-144">Vytvoření, výběr, přejmenování a odebrání kontextů</span><span class="sxs-lookup"><span data-stu-id="e2488-144">Creating, selecting, renaming, and removing contexts</span></span>

<span data-ttu-id="e2488-145">Pokud chcete vytvořit kontext, musíte být přihlášeni k Azure.</span><span class="sxs-lookup"><span data-stu-id="e2488-145">To create a context, you must be logged in to Azure.</span></span> <span data-ttu-id="e2488-146">Rutina `Add-AzureRmAccount` (nebo její alias `Login-AzureRmAccount`) nastaví výchozí kontext používaný dalšími rutinami Azure PowerShellu a umožňuje přístup ke všem tenantům a předplatným, které povolují vaše přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="e2488-146">The `Add-AzureRmAccount` cmdlet (or its alias, `Login-AzureRmAccount`) sets the default context used by subsequent Azure PowerShell cmdlets, and allows you to access any tenants or subscriptions allowed by your login credentials.</span></span>

<span data-ttu-id="e2488-147">Pokud chcete po přihlášení přidat nový kontext, použijte rutinu `Set-AzureRmContext` (nebo její alias `Select-AzureRmSubscription`).</span><span class="sxs-lookup"><span data-stu-id="e2488-147">To add a new context after login, use `Set-AzureRmContext` (or its alias, `Select-AzureRmSubscription`).</span></span>

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

<span data-ttu-id="e2488-148">Předchozí příklad přidá nový kontext s cílem Contoso Subscription 1 s použitím vašich aktuálních přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="e2488-148">The previous example adds a new context targeting 'Contoso Subscription 1' using your current credentials.</span></span> <span data-ttu-id="e2488-149">Nový kontext se pojmenuje Contoso1.</span><span class="sxs-lookup"><span data-stu-id="e2488-149">The new context is named 'Contoso1'.</span></span> <span data-ttu-id="e2488-150">Pokud pro kontext nezadáte název, použije se výchozí název vycházející z ID účtu a ID předplatného.</span><span class="sxs-lookup"><span data-stu-id="e2488-150">If you do not provide a name for the context, a default name, using the account ID and subscription ID is used.</span></span>

<span data-ttu-id="e2488-151">Pokud chcete přejmenovat existující kontext, použijte rutinu `Rename-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="e2488-151">To rename an existing context, use the `Rename-AzureRmContext` cmdlet.</span></span> <span data-ttu-id="e2488-152">Například:</span><span class="sxs-lookup"><span data-stu-id="e2488-152">For example:</span></span>

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

<span data-ttu-id="e2488-153">Tento příklad přejmenuje kontext s automaticky nastaveným názvem `[user1@contoso.org; 123456-7890-1234-564321]` na jednodušší název Contoso2.</span><span class="sxs-lookup"><span data-stu-id="e2488-153">This example renames the context with automatic name `[user1@contoso.org; 123456-7890-1234-564321]` to the simple name 'Contoso2'.</span></span> <span data-ttu-id="e2488-154">Rutiny určené pro správu kontextů také používají dokončování pomocí tabulátoru umožňující rychlý výběr kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-154">Cmdlets that manage contexts also use tab completion, allowing you to quickly select the context.</span></span>

<span data-ttu-id="e2488-155">Pokud chcete nakonec odebrat kontext, použijte rutinu `Remove-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="e2488-155">Finally, to remove a context, use the `Remove-AzureRmContext` cmdlet.</span></span>  <span data-ttu-id="e2488-156">Například:</span><span class="sxs-lookup"><span data-stu-id="e2488-156">For example:</span></span>

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

<span data-ttu-id="e2488-157">Zapomene kontext s názvem Contoso2.</span><span class="sxs-lookup"><span data-stu-id="e2488-157">Forgets the context that was named 'Contoso2'.</span></span> <span data-ttu-id="e2488-158">Následně můžete tento kontext znovu vytvořit pomocí `Set-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="e2488-158">You can recreate this context subsequently using `Set-AzureRmContext`</span></span>

## <a name="removing-credentials"></a><span data-ttu-id="e2488-159">Odebrání přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="e2488-159">Removing credentials</span></span>

<span data-ttu-id="e2488-160">Všechny přihlašovací údaje a kontexty přidružené k uživateli nebo instančnímu objektu můžete odebrat pomocí `Remove-AzureRmAccount` (označuje se také jako `Logout-AzureRmAccount`).</span><span class="sxs-lookup"><span data-stu-id="e2488-160">You can remove all credentials and associated contexts for a user or service principal using `Remove-AzureRmAccount` (also known as `Logout-AzureRmAccount`).</span></span> <span data-ttu-id="e2488-161">Pokud se rutina `Remove-AzureRmAccount` provede bez parametrů, odebere všechny přihlašovací údaje a kontexty přidružené k uživateli nebo instančnímu objektu v aktuálním kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-161">When executed without parameters, the `Remove-AzureRmAccount` cmdlet removes all credentials and contexts associated with the User or Service Principal in the current context.</span></span> <span data-ttu-id="e2488-162">Pokud chcete cílit na konkrétní instanční objekt, můžete předat uživatelské jméno, hlavní název služby (SPN) nebo kontext.</span><span class="sxs-lookup"><span data-stu-id="e2488-162">You may pass in a Username, Service Principal Name, or context to target a particular principal.</span></span>

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a><span data-ttu-id="e2488-163">Používání rozsahů kontextu</span><span class="sxs-lookup"><span data-stu-id="e2488-163">Using context scopes</span></span>

<span data-ttu-id="e2488-164">Občas můžete chtít vybrat, změnit nebo odebrat kontext v relaci PowerShellu, aniž by to ovlivnilo ostatní relace.</span><span class="sxs-lookup"><span data-stu-id="e2488-164">Occasionally, you may want to select, change, or remove a context in a PowerShell session without impacting other sessions.</span></span> <span data-ttu-id="e2488-165">Pokud chcete změnit výchozí chování rutin pracujících s kontextem, použijte parametr `Scope`.</span><span class="sxs-lookup"><span data-stu-id="e2488-165">To change the default behavior of context cmdlets, use the `Scope` parameter.</span></span> <span data-ttu-id="e2488-166">Rozsah `Process` přepíše výchozí chování tak, že se bude vztahovat pouze na aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="e2488-166">The `Process` scope overrides the default behavior by making it apply only for the current session.</span></span> <span data-ttu-id="e2488-167">Naopak rozsah `CurrentUser` změní kontext ve všech relacích, a ne pouze v aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="e2488-167">Conversely `CurrentUser` scope changes the context in all sessions, instead of just the current session.</span></span>

<span data-ttu-id="e2488-168">Například pokud chcete změnit výchozí kontext v aktuální relaci PowerShellu, aniž by to ovlivnilo ostatní okna, nebo kontext, který se použije při dalším otevření relace, použijte:</span><span class="sxs-lookup"><span data-stu-id="e2488-168">As an example, to change the default context in the current PowerShell session without impacting other windows, or the context used the next time a session is opened, use:</span></span>

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a><span data-ttu-id="e2488-169">Způsob zapamatování nastavení automatického ukládání kontextu</span><span class="sxs-lookup"><span data-stu-id="e2488-169">How the context autosave setting is remembered</span></span>

<span data-ttu-id="e2488-170">Nastavení automatického ukládání kontextu se ukládá do uživatelského adresáře Azure PowerShellu (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="e2488-170">The context AutoSave setting is saved to the user Azure PowerShell directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span> <span data-ttu-id="e2488-171">Některé druhy účtů počítače k tomuto adresáři nemusejí mít přístup.</span><span class="sxs-lookup"><span data-stu-id="e2488-171">Some kinds of computer accounts may not have access to this directory.</span></span> <span data-ttu-id="e2488-172">Pro takové scénáře můžete použít proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e2488-172">For such scenarios, you can use the environment variable</span></span>

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

<span data-ttu-id="e2488-173">Pokud je nastavena na true, kontext se automaticky uloží.</span><span class="sxs-lookup"><span data-stu-id="e2488-173">If set to 'true', the context is automatically saved.</span></span> <span data-ttu-id="e2488-174">Pokud je nastavena na false, kontext se neuloží.</span><span class="sxs-lookup"><span data-stu-id="e2488-174">If set to 'false', the context is not saved.</span></span>

## <a name="changes-to-the-azurermprofile-module"></a><span data-ttu-id="e2488-175">Změny modulu AzureRM.Profile</span><span class="sxs-lookup"><span data-stu-id="e2488-175">Changes to the AzureRM.Profile module</span></span>

<span data-ttu-id="e2488-176">Nové rutiny pro správu kontextu</span><span class="sxs-lookup"><span data-stu-id="e2488-176">New cmdlets for managing context</span></span>

- <span data-ttu-id="e2488-177">[Enable-AzureRmContextAutosave][enable] – Povolení ukládání kontextu mezi relacemi PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e2488-177">[Enable-AzureRmContextAutosave][enable] - Allow saving the context between powershell sessions.</span></span>
  <span data-ttu-id="e2488-178">Všechny změny mění globální kontext.</span><span class="sxs-lookup"><span data-stu-id="e2488-178">Any changes alter the global context.</span></span>
- <span data-ttu-id="e2488-179">[Disable-AzureRmContextAutosave][disable] – Vypnutí automatického ukládání kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-179">[Disable-AzureRmContextAutosave][disable] - Turn off autosaving the context.</span></span> <span data-ttu-id="e2488-180">V každé nové relaci PowerShellu se vyžaduje opětovné přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e2488-180">Each new PowerShell session is required to log in again.</span></span>
- <span data-ttu-id="e2488-181">[Select-AzureRmContext][select] – Výběr kontextu jako výchozího.</span><span class="sxs-lookup"><span data-stu-id="e2488-181">[Select-AzureRmContext][select] - Select a context as the default.</span></span> <span data-ttu-id="e2488-182">Všechny další rutiny k ověřování používají přihlašovací údaje v tomto kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-182">All subsequent cmdlets use the credentials in this context for authentication.</span></span>
- <span data-ttu-id="e2488-183">[Remove-AzureRmAccount][remove-cred] – Odebrání všech přihlašovacích údajů a kontextů přidružených k účtu.</span><span class="sxs-lookup"><span data-stu-id="e2488-183">[Remove-AzureRmAccount][remove-cred] - Remove all credentials and contexts associated with an account.</span></span>
- <span data-ttu-id="e2488-184">[Remove-AzureRmContext][remove-context] – Odebrání pojmenovaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-184">[Remove-AzureRmContext][remove-context] - Remove a named context.</span></span>
- <span data-ttu-id="e2488-185">[Rename-AzureRmContext][rename] – Odebrání existujícího kontextu.</span><span class="sxs-lookup"><span data-stu-id="e2488-185">[Rename-AzureRmContext][rename] - Rename an existing context.</span></span>

<span data-ttu-id="e2488-186">Změny existujících rutin pracujících s profilem</span><span class="sxs-lookup"><span data-stu-id="e2488-186">Changes to existing profile cmdlets</span></span>

- <span data-ttu-id="e2488-187">[Add-AzureRmAccount][login] – Povolení nastavení rozsahu přihlášení na příslušný proces nebo aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2488-187">[Add-AzureRmAccount][login] - Allow scoping of the login to the process or the current user.</span></span>
  <span data-ttu-id="e2488-188">Povolení pojmenování výchozího kontextu po přihlášení.</span><span class="sxs-lookup"><span data-stu-id="e2488-188">Allow naming the default context after login.</span></span>
- <span data-ttu-id="e2488-189">[Import-AzureRmContext][import] – Povolení nastavení rozsahu přihlášení na příslušný proces nebo aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2488-189">[Import-AzureRmContext][import] - Allow scoping of the login to the process or the current user.</span></span>
- <span data-ttu-id="e2488-190">[Set-AzureRmContext][set-context] – Povolení výběru existujících pojmenovaných kontextů a změna rozsahu na příslušný proces nebo aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="e2488-190">[Set-AzureRmContext][set-context] - Allow selection of existing named contexts, and scope changes to the process or current user.</span></span>

<!-- Hyperlinks -->
[enable]: /powershell/module/azurerm.profile/Enable-AzureRmContextAutosave
[disable]: /powershell/module/azurerm.profile/Disable-AzureRmContextAutosave
[select]: /powershell/module/azurerm.profile/Select-AzureRmContext
[remove-cred]: /powershell/module/azurerm.profile/Remove-AzureRmAccount
[remove-context]: /powershell/module/azurerm.profile/Remove-AzureRmContext
[rename]: /powershell/module/azurerm.profile/Rename-AzureRmContext

<!-- Updated cmdlets -->
[login]: /powershell/module/azurerm.profile/Add-AzureRmAccount
[import]: /powershell/module/azurerm.profile/Import-AzureRmAccount
[set-context]: /powershell/module/azurerm.profile/Import-AzureRmContext

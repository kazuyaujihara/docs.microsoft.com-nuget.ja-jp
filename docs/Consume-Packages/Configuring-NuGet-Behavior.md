---
title: NuGet の動作を構成する | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/25/2017
ms.topic: article
ms.prod: nuget
ms.technology: ''
description: NuGet.Config ファイルは、グローバルとプロジェクト単位の両方で NuGet の動作を制御し、変更するには nuget config コマンドを使います。
keywords: NuGet 構成ファイル, NuGet の構成, NuGet の動作の設定, NuGet の設定, Nuget.Config, NuGetDefaults.Config, 既定値
ms.reviewer:
- karann-msft
- unniravindranathan
ms.workload:
- dotnet
- aspnet
ms.openlocfilehash: 88f10cf15e16013ac99f315e572f932fd3948f73
ms.sourcegitcommit: ecb598c790d4154366bc92757ec7db1a51c34faf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="configuring-nuget-behavior"></a><span data-ttu-id="f44be-104">NuGet の動作を構成する</span><span class="sxs-lookup"><span data-stu-id="f44be-104">Configuring NuGet behavior</span></span>

<span data-ttu-id="f44be-105">NuGet の動作は、1 つ以上の `NuGet.Config` (XML) ファイルの設定を総合して決まります。ファイルは、プロジェクト レベル、ユーザー レベル、およびコンピューター全体レベルで作成できます。</span><span class="sxs-lookup"><span data-stu-id="f44be-105">NuGet's behavior is driven by the accumulated settings in one or more `NuGet.Config` (XML) files that can exist at project-, user-, and computer-wide levels.</span></span> <span data-ttu-id="f44be-106">具体的には、グローバル `NuGetDefaults.Config` ファイルでパッケージ ソースも構成されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-106">A global `NuGetDefaults.Config` file also specifically configures package sources.</span></span> <span data-ttu-id="f44be-107">設定は、CLI、パッケージ マネージャー コンソール、パッケージ マネージャー UI で発行されるすべてのコマンドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-107">Settings apply to all commands issued in the CLI, the Package Manager Console, and the Package Manager UI.</span></span>

## <a name="config-file-locations-and-uses"></a><span data-ttu-id="f44be-108">構成ファイルの場所と使用</span><span class="sxs-lookup"><span data-stu-id="f44be-108">Config file locations and uses</span></span>

| <span data-ttu-id="f44be-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="f44be-109">Scope</span></span> | <span data-ttu-id="f44be-110">NuGet.Config ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="f44be-110">NuGet.Config file location</span></span> | <span data-ttu-id="f44be-111">説明</span><span class="sxs-lookup"><span data-stu-id="f44be-111">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f44be-112">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f44be-112">Project</span></span> | <span data-ttu-id="f44be-113">現在のフォルダー (プロジェクト フォルダーとも呼ばれる) またはドライブのルートまでの任意のフォルダー。</span><span class="sxs-lookup"><span data-stu-id="f44be-113">Current folder (aka Project folder) or any folder up to the drive root.</span></span>| <span data-ttu-id="f44be-114">プロジェクト フォルダーにある場合は、設定はそのプロジェクトのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-114">In a project folder, settings apply only to that project.</span></span> <span data-ttu-id="f44be-115">複数のプロジェクト サブフォルダーを含む親フォルダーにある場合は、設定はそれらのサブフォルダーのすべてのプロジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-115">In parent folders that contain multiple projects subfolders, settings apply to all projects in those subfolders.</span></span> |
| <span data-ttu-id="f44be-116">ユーザー</span><span class="sxs-lookup"><span data-stu-id="f44be-116">User</span></span> | <span data-ttu-id="f44be-117">Windows: `%appdata%\NuGet\NuGet.Config`</span><span class="sxs-lookup"><span data-stu-id="f44be-117">Windows: `%appdata%\NuGet\NuGet.Config`</span></span><br/><span data-ttu-id="f44be-118">Mac/Linux: `~/.config/NuGet/NuGet.Config` または `~/.nuget/NuGet/NuGet.Config` (OS のディストリビューションによって異なります)</span><span class="sxs-lookup"><span data-stu-id="f44be-118">Mac/Linux: `~/.config/NuGet/NuGet.Config` or `~/.nuget/NuGet/NuGet.Config` (varies by OS distribution)</span></span> | <span data-ttu-id="f44be-119">設定はすべての操作に適用されますが、プロジェクト レベルの設定によって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="f44be-119">Settings apply to all operations, but are overridden by any project-level settings.</span></span> |
| <span data-ttu-id="f44be-120">コンピューター</span><span class="sxs-lookup"><span data-stu-id="f44be-120">Computer</span></span> | <span data-ttu-id="f44be-121">Windows: `%ProgramFiles(x86)%\NuGet\Config`</span><span class="sxs-lookup"><span data-stu-id="f44be-121">Windows: `%ProgramFiles(x86)%\NuGet\Config`</span></span><br/><span data-ttu-id="f44be-122">Mac/Linux: `$XDG_DATA_HOME`。</span><span class="sxs-lookup"><span data-stu-id="f44be-122">Mac/Linux: `$XDG_DATA_HOME`.</span></span> <span data-ttu-id="f44be-123">`$XDG_DATA_HOME` が null または空の場合は、`~/.local/share` または `/usr/local/share` が使用されます (OS 配布によって異なります)</span><span class="sxs-lookup"><span data-stu-id="f44be-123">If `$XDG_DATA_HOME` is null or empty, `~/.local/share` or `/usr/local/share` will be used (varies by OS distribution)</span></span>  | <span data-ttu-id="f44be-124">設定はそのコンピューターでのすべての操作に適用されますが、ユーザー レベルまたはプロジェクト レベルの設定によって上書きされます。</span><span class="sxs-lookup"><span data-stu-id="f44be-124">Settings apply to all operations on the computer, but are overridden by any user- or project-level settings.</span></span> |

<span data-ttu-id="f44be-125">以前のバージョンの NuGet に関する注意事項:</span><span class="sxs-lookup"><span data-stu-id="f44be-125">Notes for earlier versions of NuGet:</span></span>
- <span data-ttu-id="f44be-126">NuGet 3.3 以前では、ソリューション全体の設定用に `.nuget` フォルダーが使われていました。</span><span class="sxs-lookup"><span data-stu-id="f44be-126">NuGet 3.3 and earlier used a `.nuget` folder for solution-wide settings.</span></span> <span data-ttu-id="f44be-127">このファイルは、NuGet 3.4 以降では使用されません。</span><span class="sxs-lookup"><span data-stu-id="f44be-127">This file is not used in NuGet 3.4+.</span></span>
- <span data-ttu-id="f44be-128">NuGet 2.6 から 3.x では、Windows でのコンピューター レベルの構成ファイルは %ProgramData%\NuGet\Config[\\{IDE}[\\{Version}[\\{SKU}]]]\NuGet.Config にありました。*{IDE}* には *VisualStudio* を使用でき、*{Version}* は Visual Studio のバージョン (*14.0* など)、*{SKU}* は *Community*、*Pro*、または *Enterprise* です。</span><span class="sxs-lookup"><span data-stu-id="f44be-128">For NuGet 2.6 to 3.x, the computer-level config file on Windows was located in %ProgramData%\NuGet\Config[\\{IDE}[\\{Version}[\\{SKU}]]]\NuGet.Config, where *{IDE}* can be *VisualStudio*, *{Version}* was the Visual Studio version such as *14.0*, and *{SKU}* is either *Community*, *Pro*, or *Enterprise*.</span></span> <span data-ttu-id="f44be-129">設定を NuGet 4.0 以降に移行するには、単に構成ファイルを %ProgramFiles(x86)%\NuGet\Config にコピーします。Linux の以前の場所は /etc/opt、Mac の以前の場所は /Library/Application Support でした。</span><span class="sxs-lookup"><span data-stu-id="f44be-129">To migrate settings to NuGet 4.0+, simply copy the config file to %ProgramFiles(x86)%\NuGet\Config. On Linux, this previous location was /etc/opt, and on Mac, /Library/Application Support.</span></span>

## <a name="changing-config-settings"></a><span data-ttu-id="f44be-130">構成設定の変更</span><span class="sxs-lookup"><span data-stu-id="f44be-130">Changing config settings</span></span>

<span data-ttu-id="f44be-131">`NuGet.Config` ファイルは、[NuGet の構成設定](../reference/nuget-config-file.md)に関するトピックで説明されているように、キーと値のペアを含む単純な XML テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="f44be-131">A `NuGet.Config` file is a simple XML text file containing key/value pairs as described in the [NuGet Configuration Settings](../reference/nuget-config-file.md) topic.</span></span>

<span data-ttu-id="f44be-132">設定は、NuGet CLI の [config コマンド](../tools/cli-ref-config.md)を使って管理します。</span><span class="sxs-lookup"><span data-stu-id="f44be-132">Settings are managed using the NuGet CLI [config command](../tools/cli-ref-config.md):</span></span>
- <span data-ttu-id="f44be-133">既定では、変更はユーザー レベルの構成ファイルに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="f44be-133">By default, changes are made to the user-level config file.</span></span>
- <span data-ttu-id="f44be-134">別のファイルの設定を変更するには、`-configFile` スイッチを使います。</span><span class="sxs-lookup"><span data-stu-id="f44be-134">To change settings in a different file, use the `-configFile` switch.</span></span> <span data-ttu-id="f44be-135">その場合は、任意のファイル名を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-135">In this case files can use any filename.</span></span>
- <span data-ttu-id="f44be-136">キーは常に大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-136">Keys are always case sensitive.</span></span>
- <span data-ttu-id="f44be-137">コンピューター レベルの設定ファイルの設定を変更するには、特権の昇格が必要です。</span><span class="sxs-lookup"><span data-stu-id="f44be-137">Elevation is required to change settings in the computer-level settings file.</span></span>

> [!Warning]
> <span data-ttu-id="f44be-138">任意のテキスト エディターでファイルを変更できますが、NuGet (v3.4.3 以降) では、構成ファイルに正しくない形式の XML (タグの不一致、無効な引用符など) が含まれると、警告なしに構成ファイル全体が無視されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-138">Although you can modify the file in any text editor, NuGet (v3.4.3 and later) silently ignores the entire configuration file if it contains malformed XML (mismatched tags, invalid quotation marks, etc.).</span></span> <span data-ttu-id="f44be-139">このため、設定の管理には `nuget config` を使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f44be-139">This is why it's preferable to manage setting using `nuget config`.</span></span>

### <a name="setting-a-value"></a><span data-ttu-id="f44be-140">値の設定</span><span class="sxs-lookup"><span data-stu-id="f44be-140">Setting a value</span></span>

<span data-ttu-id="f44be-141">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="f44be-141">Windows:</span></span>

```cli
# Set repositoryPath in the user-level config file
nuget config -set repositoryPath=c:\packages 

# Set repositoryPath in project-level files
nuget config -set repositoryPath=c:\packages -configfile c:\my.Config
nuget config -set repositoryPath=c:\packages -configfile .\myApp\NuGet.Config

# Set repositoryPath in the computer-level file (requires elevation)
nuget config -set repositoryPath=c:\packages -configfile %ProgramFiles(x86)%\NuGet\NuGet.Config
```

<span data-ttu-id="f44be-142">Mac/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="f44be-142">Mac/Linux:</span></span>

```cli
# Set repositoryPath in the user-level config file
nuget config -set repositoryPath=/home/packages 

# Set repositoryPath in project-level files
nuget config -set repositoryPath=/home/projects/packages -configfile /home/my.Config
nuget config -set repositoryPath=/home/packages -configfile home/myApp/NuGet.Config

# Set repositoryPath in the computer-level file (requires elevation)
nuget config -set repositoryPath=/home/packages -configfile $XDG_DATA_HOME/NuGet.Config
```

> [!Note]
> <span data-ttu-id="f44be-143">NuGet 3.4 以降では、`repositoryPath=%PACKAGEHOME%` (Windows) および `repositoryPath=%PACKAGEHOME` (Mac/Linux) のように、すべての値で環境変数を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-143">In NuGet 3.4 and later you can use environment variables in any value, as in `repositoryPath=%PACKAGEHOME%` (Windows) and `repositoryPath=%PACKAGEHOME` (Mac/Linux).</span></span>

### <a name="removing-a-value"></a><span data-ttu-id="f44be-144">値の削除</span><span class="sxs-lookup"><span data-stu-id="f44be-144">Removing a value</span></span>

<span data-ttu-id="f44be-145">値を削除するには、値を空にしてキーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f44be-145">To remove a value, specify a key with an empty value.</span></span>

```cli
# Windows
nuget config -set repositoryPath= -configfile c:\my.Config

# Mac/Linux
nuget config -set repositoryPath= -configfile /home/my.Config
```

### <a name="creating-a-new-config-file"></a><span data-ttu-id="f44be-146">新しい構成ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f44be-146">Creating a new config file</span></span>

<span data-ttu-id="f44be-147">次のテンプレートを新しいファイルにコピーした後、`nuget config -configFile <filename>` を使って値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f44be-147">Copy the template below into the new file and then use `nuget config -configFile <filename>` to set values:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
</configuration>
```

## <a name="how-settings-are-applied"></a><span data-ttu-id="f44be-148">設定の適用方法</span><span class="sxs-lookup"><span data-stu-id="f44be-148">How settings are applied</span></span>

<span data-ttu-id="f44be-149">複数の `NuGet.Config` ファイルを使って設定を異なる場所に格納することで、1 つのプロジェクト、プロジェクトのグループ、またはすべてのプロジェクトに設定を適用できます。</span><span class="sxs-lookup"><span data-stu-id="f44be-149">Multiple `NuGet.Config` files allow you to store settings in different locations so that they apply to a single project, a group of projects, or all projects.</span></span> <span data-ttu-id="f44be-150">これらの設定は、コマンド ラインまたは Visual Studio から呼び出されるすべての NuGet 操作に集合的に適用され、プロジェクトまたは現在のフォルダーの "最も近く" に存在する設定が優先されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-150">These settings collectively apply to any NuGet operation invoked from the command line or from Visual Studio, with settings that exist "closest" to a project or the current folder taking precedence.</span></span>

<span data-ttu-id="f44be-151">具体的には、NuGet は次の順序で異なる構成ファイルから設定を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f44be-151">Specifically, NuGet loads settings from the different config files in the following order:</span></span>

1. <span data-ttu-id="f44be-152">[NuGetDefaults.Config ファイル](#nuget-defaults-file)。パッケージ ソースのみに関連する設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f44be-152">The [NuGetDefaults.Config file](#nuget-defaults-file), which contains settings related only to package sources.</span></span>
1. <span data-ttu-id="f44be-153">コンピューター レベルのファイル。</span><span class="sxs-lookup"><span data-stu-id="f44be-153">The computer-level file.</span></span>
1. <span data-ttu-id="f44be-154">ユーザー レベルのファイル。</span><span class="sxs-lookup"><span data-stu-id="f44be-154">The user-level file.</span></span>
1. <span data-ttu-id="f44be-155">`-configFile` で指定されたファイル。</span><span class="sxs-lookup"><span data-stu-id="f44be-155">The file specified with `-configFile`.</span></span>
1. <span data-ttu-id="f44be-156">ドライブ ルートから現在のフォルダー (nuget.exe が呼び出されたフォルダー、または Visual Studio プロジェクトを含むフォルダー) までの間のパスに存在するすべてのフォルダーで見つかったファイル。</span><span class="sxs-lookup"><span data-stu-id="f44be-156">Files found in every folder in the path from the drive root to the current folder (where nuget.exe is invoked or the folder containing the Visual Studio project).</span></span> <span data-ttu-id="f44be-157">たとえば、コマンドが c:\A\B\C で呼び出された場合、NuGet は c:\,、c:\A、c:\A\B、c:\A\B\C の順序で構成ファイルを探して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f44be-157">For example, if a command is invoked in c:\A\B\C, NuGet looks for and loads config files in c:\, then c:\A, then c:\A\B, and finally c:\A\B\C.</span></span>

<span data-ttu-id="f44be-158">NuGet はこれらのファイルで設定を探すので、適用は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f44be-158">As NuGet finds settings in these files, they are applied as follows:</span></span>

1. <span data-ttu-id="f44be-159">単一項目の要素の場合は、前に検出された同じキーの値が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="f44be-159">For single-item elements, NuGet replaced any previously-found value for the same key.</span></span> <span data-ttu-id="f44be-160">つまり、現在のフォルダーまたはプロジェクトに "最も近い" 設定が、それより前に見つかった他の値を上書きします。</span><span class="sxs-lookup"><span data-stu-id="f44be-160">This means that settings that are "closest" to the current folder or project override any others found earlier.</span></span> <span data-ttu-id="f44be-161">たとえば、`NuGetDefaults.Config` の設定 `defaultPushSource` は、他の構成ファイルにも存在する場合は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="f44be-161">For example, the `defaultPushSource` setting in `NuGetDefaults.Config` is overridden if it exists in any other config file.</span></span>

1. <span data-ttu-id="f44be-162">コレクション要素の場合は (`<packageSources>` など)、すべての構成ファイルの値が 1 つのコレクションに結合されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-162">For collection elements (such as `<packageSources>`), NuGet combines the values from all configuration files into a single collection.</span></span>

1. <span data-ttu-id="f44be-163">指定されたノードに `<clear />` が存在すると、そのノードより前に定義された構成値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-163">When `<clear />` is present for a given node, NuGet ignores previously defined configuration values for that node.</span></span>

### <a name="settings-walkthrough"></a><span data-ttu-id="f44be-164">設定のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="f44be-164">Settings walkthrough</span></span>

<span data-ttu-id="f44be-165">2 つの異なるドライブに次のフォルダー構造があるものとします。</span><span class="sxs-lookup"><span data-stu-id="f44be-165">Let's say you have the following folder structure on two separate drives:</span></span>

    disk_drive_1
        User
    disk_drive_2
       Project1
         Source
       Project2
         Source
       tmp

<span data-ttu-id="f44be-166">その場合、次の場所にそれぞれ指定された内容の `NuGet.Config` ファイルが 4 つ存在します </span><span class="sxs-lookup"><span data-stu-id="f44be-166">You then have four `NuGet.Config` files in the following locations with the given content.</span></span> <span data-ttu-id="f44be-167">(コンピューター レベルのファイルはこの例には含まれませんが、ユーザー レベルのファイルと同じように動作します)。</span><span class="sxs-lookup"><span data-stu-id="f44be-167">(The computer-level file is not included in this example, but would behave similarly to the user-level file.)</span></span>

<span data-ttu-id="f44be-168">ファイル A. ユーザーレベルのファイル (Windows では `%appdata%\NuGet\NuGet.Config`、Mac/Linux では `~/.config/NuGet/NuGet.Config`):</span><span class="sxs-lookup"><span data-stu-id="f44be-168">File A. User-level file, (`%appdata%\NuGet\NuGet.Config` on Windows, `~/.config/NuGet/NuGet.Config` on Mac/Linux):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <activePackageSource>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
    </activePackageSource>
</configuration>
```

<span data-ttu-id="f44be-169">ファイル B: disk_drive_2/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="f44be-169">File B. disk_drive_2/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <add key="repositoryPath" value="disk_drive_2/tmp" />
    </config>
    <packageRestore>
        <add key="enabled" value="True" />
    </packageRestore>
</configuration>
```

<span data-ttu-id="f44be-170">ファイル C: disk_drive_2/Project1/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="f44be-170">File C. disk_drive_2/Project1/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <add key="repositoryPath" value="External/Packages" />
        <add key="defaultPushSource" value="https://MyPrivateRepo/ES/api/v2/package" />
    </config>
    <packageSources>
        <clear /> <!-- ensure only the sources defined below are used -->
        <add key="MyPrivateRepo - ES" value="https://MyPrivateRepo/ES/nuget" />
    </packageSources>
</configuration>
```

<span data-ttu-id="f44be-171">ファイル D: disk_drive_2/Project2/NuGet.Config:</span><span class="sxs-lookup"><span data-stu-id="f44be-171">File D. disk_drive_2/Project2/NuGet.Config:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <packageSources>
        <!-- Add this repository to the list of available repositories -->
        <add key="MyPrivateRepo - DQ" value="https://MyPrivateRepo/DQ/nuget" />
    </packageSources>
</configuration>
```

<span data-ttu-id="f44be-172">NuGet は、呼び出された場所に応じて、次のように設定を読み込んで適用します。</span><span class="sxs-lookup"><span data-stu-id="f44be-172">NuGet then loads and applies settings as follows, depending on where it's invoked:</span></span>

- <span data-ttu-id="f44be-173">**disk_drive_1/users から呼び出された場合**: disk_drive_1 で検出されるのはユーザー レベルの構成ファイル (A) だけなので、(A) で指定されている既定のリポジトリのみが使われます。</span><span class="sxs-lookup"><span data-stu-id="f44be-173">**Invoked from disk_drive_1/users**: Only the default repository listed in the user-level configuration file (A) is used, because that's the only file found on disk_drive_1.</span></span>

- <span data-ttu-id="f44be-174">**disk_drive_2/ または disk_drive_/tmp から呼び出された場合**: NuGet は、最初にユーザー レベルのファイル (A) を読み込んだ後、disk_drive_2 のルートに移動して、ファイル (B) を検出します。</span><span class="sxs-lookup"><span data-stu-id="f44be-174">**Invoked from disk_drive_2/ or disk_drive_/tmp**: The user-level file (A) is loaded first, then NuGet goes to the root of disk_drive_2 and finds file (B).</span></span> <span data-ttu-id="f44be-175">NuGet は /tmp でも構成ファイルを検索しますが、見つかりません。</span><span class="sxs-lookup"><span data-stu-id="f44be-175">NuGet also looks for a configuration file in /tmp but does not find one.</span></span> <span data-ttu-id="f44be-176">その結果、nuget.org の既定のリポジトリが使われ、パッケージの復元が有効になり、パッケージが disk_drive_2/tmp に展開されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-176">As a result, the default repository on nuget.org is used, package restore is enabled, and packages get expanded in disk_drive_2/tmp.</span></span>

- <span data-ttu-id="f44be-177">**disk_drive_2/Project1 または disk_drive_2/Project1/Source から呼び出された場合**: NuGet は、最初にユーザー レベルのファイル (A) を読み込み、次に disk_drive_2 のルートからファイル (B) を読み込み、最後にファイル (C) を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f44be-177">**Invoked from disk_drive_2/Project1 or disk_drive_2/Project1/Source**: The user-level file (A) is loaded first, then NuGet loads file (B) from the root of disk_drive_2, followed by file (C).</span></span> <span data-ttu-id="f44be-178">(C) の設定で (B) および (A) の設定が上書きされるので、パッケージがインストールされる `repositoryPath` は、*disk_drive_2/tmp* ではなく disk_drive_2/Project1/External/Packages です。</span><span class="sxs-lookup"><span data-stu-id="f44be-178">Settings in (C) override those in (B) and (A), so the `repositoryPath` where packages get installed is disk_drive_2/Project1/External/Packages instead of *disk_drive_2/tmp*.</span></span> <span data-ttu-id="f44be-179">また、(C) は `<packageSources>` をクリアするので、ソースは `https://MyPrivateRepo/ES/nuget` だけになり、nuget.org は使うことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="f44be-179">Also, because (C) clears `<packageSources>`, nuget.org is no longer available as a source leaving only `https://MyPrivateRepo/ES/nuget`.</span></span>

- <span data-ttu-id="f44be-180">**disk_drive_2/Project2 または disk_drive_2/Project2/Source から呼び出された場合**: ユーザー レベルのファイル (A)、ファイル (B)、ファイル (D) の順に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f44be-180">**Invoked from disk_drive_2/Project2 or disk_drive_2/Project2/Source**: The user-level file (A) is loaded first followed by file (B) and file (D).</span></span> <span data-ttu-id="f44be-181">`packageSources` はクリアされないので、`nuget.org` と `https://MyPrivateRepo/DQ/nuget` の両方をソースとして使うことができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-181">Because `packageSources` is not cleared, both `nuget.org` and `https://MyPrivateRepo/DQ/nuget` are available as sources.</span></span> <span data-ttu-id="f44be-182">パッケージは、(B) で指定されている disk_drive_2/tmp に展開されます。</span><span class="sxs-lookup"><span data-stu-id="f44be-182">Packages get expanded in disk_drive_2/tmp as specified in (B).</span></span>

## <a name="nuget-defaults-file"></a><span data-ttu-id="f44be-183">NuGet の既定のファイル</span><span class="sxs-lookup"><span data-stu-id="f44be-183">NuGet defaults file</span></span>

<span data-ttu-id="f44be-184">パッケージのインストール元および更新元であるパッケージ ソースを指定し、`nuget push` でパッケージを公開するときの既定のターゲットを制御するため、`NuGetDefaults.Config` ファイルが存在します。</span><span class="sxs-lookup"><span data-stu-id="f44be-184">The `NuGetDefaults.Config` file exists to specify package sources from which packages are installed and updated, and to control the default target for publishing packages with `nuget push`.</span></span> <span data-ttu-id="f44be-185">管理者は開発用およびビルド用のコンピューターに整合性のある `NuGetDefaults.Config` ファイルを容易に (たとえば、グループ ポリシーを使って) 展開できるので、組織内のすべてのユーザーが nuget.org ではなく適切なパッケージ ソースを使うようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-185">Because administrators can conveniently (using Group Policy, for example) deploy consistent `NuGetDefaults.Config` files to developer and build machines, they can ensuring that everyone in the organization is using the correct package sources rather than nuget.org.</span></span>

> [!Important]
> <span data-ttu-id="f44be-186">`NuGetDefaults.Config` ファイルにより、パッケージ ソースが開発者の NuGet 構成から削除されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f44be-186">The `NuGetDefaults.Config` file never causes a package source to be removed from a developer's NuGet configuration.</span></span> <span data-ttu-id="f44be-187">つまり、開発者が既に NuGet を使っていて、したがって nuget.org パッケージ ソースが登録されている場合、`NuGetDefaults.Config` ファイルの作成後に nuget.org は削除されません。</span><span class="sxs-lookup"><span data-stu-id="f44be-187">That means if the developer has already used NuGet and therefore has the nuget.org package source registered, it won't be removed after the creation of a `NuGetDefaults.Config` file.</span></span>
>
> <span data-ttu-id="f44be-188">さらに、`NuGetDefaults.Config` または NuGet の他のメカニズムのどちらでも、nuget.org などのパッケージ ソースへのアクセスを禁止することはできません。組織でこのようなアクセスをブロックする場合は、ファイアウォールなどの他の手段を使って行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f44be-188">Furthermore, neither `NuGetDefaults.Config` nor any other mechanism in NuGet can prevent access to package sources like nuget.org. If an organization wishes to block such access, it much use other means such as firewalls to do so.</span></span>

### <a name="nugetdefaultsconfig-location"></a><span data-ttu-id="f44be-189">NuGetDefaults.Config の場所</span><span class="sxs-lookup"><span data-stu-id="f44be-189">NuGetDefaults.Config location</span></span>

<span data-ttu-id="f44be-190">次の表は、ターゲットの OS に応じた `NuGetDefaults.Config` ファイルの格納場所の一覧です。</span><span class="sxs-lookup"><span data-stu-id="f44be-190">The following table describes where the `NuGetDefaults.Config` file should be stored, depending on the target OS:</span></span>

| <span data-ttu-id="f44be-191">OS プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="f44be-191">OS Platform</span></span>  | <span data-ttu-id="f44be-192">NuGetDefaults.Config の場所</span><span class="sxs-lookup"><span data-stu-id="f44be-192">NuGetDefaults.Config Location</span></span> |
| --- | --- |
| <span data-ttu-id="f44be-193">Windows</span><span class="sxs-lookup"><span data-stu-id="f44be-193">Windows</span></span>      | <span data-ttu-id="f44be-194">**Visual Studio 2017 または NuGet 4.x+:** `%ProgramFiles(x86)%\NuGet\Config`</span><span class="sxs-lookup"><span data-stu-id="f44be-194">**Visual Studio 2017 or NuGet 4.x+:** `%ProgramFiles(x86)%\NuGet\Config`</span></span> <br /><span data-ttu-id="f44be-195">**Visual Studio 2015 以前または NuGet 3.x 以前:** `%PROGRAMDATA%\NuGet`</span><span class="sxs-lookup"><span data-stu-id="f44be-195">**Visual Studio 2015 and earlier or NuGet 3.x and earlier:** `%PROGRAMDATA%\NuGet`</span></span> |
| <span data-ttu-id="f44be-196">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="f44be-196">Mac/Linux</span></span>    | <span data-ttu-id="f44be-197">`$XDG_DATA_HOME` (通常は `~/.local/share` または `/usr/local/share`。OS のディストリビューションに依存します)</span><span class="sxs-lookup"><span data-stu-id="f44be-197">`$XDG_DATA_HOME` (typically `~/.local/share` or `/usr/local/share`, depending on OS distribution)</span></span>|

### <a name="nugetdefaultsconfig-settings"></a><span data-ttu-id="f44be-198">NuGetDefaults.Config の設定</span><span class="sxs-lookup"><span data-stu-id="f44be-198">NuGetDefaults.Config settings</span></span>

- <span data-ttu-id="f44be-199">`packageSources`: このコレクションは標準の構成ファイルの `packageSources` と同じ意味であり、既定のソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="f44be-199">`packageSources`: this collection has the same meaning as `packageSources` in regular config files and specifies the default sources.</span></span> <span data-ttu-id="f44be-200">NuGet は、`packages.config` 管理形式を使用してプロジェクトのパッケージをインストールまたは更新するときに、ソースを順番に使用します。</span><span class="sxs-lookup"><span data-stu-id="f44be-200">NuGet uses the sources in order when installing or updating packages in projects using the `packages.config` management format.</span></span> <span data-ttu-id="f44be-201">PackageReference 形式を使用するプロジェクトの場合、構成ファイルの順序に関係なく、NuGet はまずローカル ソースを使用し、次にネットワーク共有のソースを使用し、次に HTTP ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="f44be-201">For projects using the PackageReference format, NuGet uses local sources first, then sources on network shares, then HTTP sources, regardless of the order in the configuration files.</span></span> <span data-ttu-id="f44be-202">復元操作の場合、NuGet はソースの順序を常に無視します。</span><span class="sxs-lookup"><span data-stu-id="f44be-202">NuGet always ignores the order of sources with restore operations.</span></span>

- <span data-ttu-id="f44be-203">`disabledPackageSources`: このコレクションも `NuGet.Config` ファイルと同じ意味であり、影響を受ける各ソースの名前と、ソースが無効かどうかを示す true/false の値を列記します。</span><span class="sxs-lookup"><span data-stu-id="f44be-203">`disabledPackageSources`: this collection also has the same meaning as in `NuGet.Config` files, where each affected source is listed by its name and a true/false value indicating whether it's disabled.</span></span> <span data-ttu-id="f44be-204">これにより、ソースの名前と URL を、既定で有効にしなくても、`packageSources` に残しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-204">This allows the source name and URL to remain in `packageSources` without having it turned on by default.</span></span> <span data-ttu-id="f44be-205">個々の開発者は、正しい URL を改めて調べなくても、他の `NuGet.Config` ファイルでソースの値を false に設定することにより、ソースを再び有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f44be-205">Individual developers can then re-enable the source by setting the source's value to false in other `NuGet.Config` files without having to find the correct URL again.</span></span> <span data-ttu-id="f44be-206">これは、組織の内部ソースの URL の完全なリストを開発者に提供しながら、既定で個別のチームのソースのみを有効にする場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="f44be-206">This is also useful to supply developers with a full list of internal source URLs for an organization while enabling only an individual team's source by default.</span></span>

- <span data-ttu-id="f44be-207">`defaultPushSource`: `nuget push` 操作の既定のターゲットを指定し、nuget.org の組み込みの既定値を上書きします。管理者がこの設定を展開すると、開発者は nuget.org に公開するには `nuget push -Source` を明示的に使う必要があるため、内部パッケージがパブリックの nuget.org に誤って公開されるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="f44be-207">`defaultPushSource`: specifies the default target for `nuget push` operations, overriding the built-in default of nuget.org. Administrators can deploy this setting to avoid publishing internal packages to the public nuget.org by accident, as developers specifically need to use `nuget push -Source` to publish to nuget.org.</span></span>

### <a name="example-nugetdefaultsconfig-and-application"></a><span data-ttu-id="f44be-208">NuGetDefaults.Config とアプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="f44be-208">Example NuGetDefaults.Config and application</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!-- defaultPushSource key works like the 'defaultPushSource' key of NuGet.Config files. -->
    <!-- This can be used by administrators to prevent accidental publishing of packages to nuget.org. -->
    <config>
        <add key="defaultPushSource" value="https://contoso.com/packages/" />
    </config>

    <!-- Default Package Sources; works like the 'packageSources' section of NuGet.Config files. -->
    <!-- This collection cannot be deleted or modified but can be disabled/enabled by users. -->
    <packageSources>
        <add key="Contoso Package Source" value="https://contoso.com/packages/" />
        <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
    </packageSources>

    <!-- Default Package Sources that are disabled by default. -->
    <!-- Works like the 'disabledPackageSources' section of NuGet.Config files. -->
    <!-- Sources cannot be modified or deleted either but can be enabled/disabled by users. -->
    <disabledPackageSources>
        <add key="nuget.org" value="true" />
    </disabledPackageSources>
</configuration>
```
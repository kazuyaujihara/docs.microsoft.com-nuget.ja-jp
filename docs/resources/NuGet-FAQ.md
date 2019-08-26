---
title: NuGet に関してよく寄せられる質問
description: コマンド ラインと Visual Studio での NuGet の使用に関する一般的な質問と回答。
author: shishirx34
ms.author: shishirh
ms.date: 06/05/2019
ms.topic: conceptual
ms.openlocfilehash: 9b12b1fa27308cf41b58b0c244ea648d3eecdc95
ms.sourcegitcommit: 7441f12f06ca380feb87c6192ec69f6108f43ee3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69520392"
---
# <a name="nuget-frequently-asked-questions"></a><span data-ttu-id="022a6-103">NuGet に関してよく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="022a6-103">NuGet frequently-asked questions</span></span>

<span data-ttu-id="022a6-104">**NuGet を実行するために必要なものは何ですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-104">**What is required to run NuGet?**</span></span>

<span data-ttu-id="022a6-105">UI とコマンド ライン ツールの両方に関するすべての情報は、[インストール ガイド](../install-nuget-client-tools.md)で入手できます。</span><span class="sxs-lookup"><span data-stu-id="022a6-105">All the information around both UI and command-line tools is available in the [Install guide](../install-nuget-client-tools.md).</span></span>

<span data-ttu-id="022a6-106">**NuGet で Mono はサポートされますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-106">**Does NuGet support Mono?**</span></span>

<span data-ttu-id="022a6-107">コマンド ライン ツール `nuget.exe` は Mono 3.2+ でビルドおよび実行され、Mono でパッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="022a6-107">The command-line tool, `nuget.exe`, builds and runs under Mono 3.2+ and can create packages in Mono.</span></span>

<span data-ttu-id="022a6-108">`nuget.exe` は Windows では完全に動作しますが、Linux と OS X では既知の問題があります。GitHub の [Mono に関する問題](https://github.com/NuGet/Home/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+mono)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-108">Although `nuget.exe` works fully on Windows, there are known issues on Linux and OS X. Refer to [Mono issues](https://github.com/NuGet/Home/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+mono) on GitHub.</span></span>

<span data-ttu-id="022a6-109">[グラフィカル クライアント](https://github.com/mrward/monodevelop-nuget-addin)は、MonoDevelop 用のアドインとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="022a6-109">A [graphical client](https://github.com/mrward/monodevelop-nuget-addin) is available as an add-in for MonoDevelop.</span></span>

<span data-ttu-id="022a6-110">**パッケージの内容と、それが自分のアプリケーションに対して安定したものであり、役立つものであるかどうかはどのように判別すればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-110">**How can I determine what a package contains and whether it's stable and useful for my application?**</span></span>

<span data-ttu-id="022a6-111">パッケージについて学習するための主なソースとして、nuget.org (または別のプライベート フィード) のリスト ページがあります。</span><span class="sxs-lookup"><span data-stu-id="022a6-111">The primary source for learning about a package is its listing page on nuget.org (or another private feed).</span></span> <span data-ttu-id="022a6-112">nuget.org の各パッケージ ページには、パッケージ、そのバージョン履歴、使用状況の統計の説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="022a6-112">Each package page on nuget.org includes a description of the package, its version history, and usage statistics.</span></span> <span data-ttu-id="022a6-113">パッケージ ページの **[情報]** セクションには、プロジェクトの Web サイトへのリンクも含まれています。通常はこのサイトで、パッケージの使用方法について学習する際に役立つ多くの例とその他のドキュメントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="022a6-113">The **Info** section on the package page also contains a link to the project's web site where you typically find many examples and other documentation to help you learn how the package is used.</span></span>

<span data-ttu-id="022a6-114">詳細については、「[パッケージの検索と選択](../consume-packages/finding-and-choosing-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-114">For more information, see [Finding and choosing packages](../consume-packages/finding-and-choosing-packages.md).</span></span>

## <a name="nuget-in-visual-studio"></a><span data-ttu-id="022a6-115">Visual Studio の NuGet</span><span class="sxs-lookup"><span data-stu-id="022a6-115">NuGet in Visual Studio</span></span>

<span data-ttu-id="022a6-116">**別の Visual Studio 製品では NuGet はどのようにサポートされますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-116">**How is NuGet supported in different Visual Studio products?**</span></span>

- <span data-ttu-id="022a6-117">Windows の Visual Studio では、[パッケージ マネージャー UI](../consume-packages/install-use-packages-visual-studio.md) と[パッケージ マネージャー コンソール](../consume-packages/install-use-packages-powershell.md)がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="022a6-117">Visual Studio on Windows supports the [Package Manager UI](../consume-packages/install-use-packages-visual-studio.md) and the [Package Manager Console](../consume-packages/install-use-packages-powershell.md).</span></span>
- <span data-ttu-id="022a6-118">「[プロジェクトに NuGet パッケージを含める](/visualstudio/mac/nuget-walkthrough)」で説明されているように、Visual Studio for Mac には NuGet 機能が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="022a6-118">Visual Studio for Mac has built-in NuGet capabilities as described on [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span>
- <span data-ttu-id="022a6-119">Visual Studio Code (すべてのプラットフォーム) には、直接 NuGet は統合されていません。</span><span class="sxs-lookup"><span data-stu-id="022a6-119">Visual Studio Code (all platforms) does not have any direct NuGet integration.</span></span> <span data-ttu-id="022a6-120">[NuGet CLI](../reference/nuget-exe-cli-reference.md) または [dotnet CLI](../reference/dotnet-commands.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-120">Use the [NuGet CLI](../reference/nuget-exe-cli-reference.md) or the [dotnet CLI](../reference/dotnet-commands.md).</span></span>
- <span data-ttu-id="022a6-121">Azure DevOps には、[NuGet パッケージを復元するためのビルド ステップ](/vsts/build-release/tasks/package/nuget)があります。</span><span class="sxs-lookup"><span data-stu-id="022a6-121">Azure DevOps provides [a build step to restore NuGet packages](/vsts/build-release/tasks/package/nuget).</span></span> <span data-ttu-id="022a6-122">[Azure DevOps でプライベート NuGet パッケージ フィードをホストする](https://docs.microsoft.com/azure/devops/artifacts/nuget/publish)こともできます。</span><span class="sxs-lookup"><span data-stu-id="022a6-122">You can also [host private NuGet package feeds on Azure DevOps](https://docs.microsoft.com/azure/devops/artifacts/nuget/publish).</span></span>

<span data-ttu-id="022a6-123">**インストールされている NuGet ツールの正確なバージョンはどのように確認すればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-123">**How do I check the exact version of the NuGet tools that are installed?**</span></span>

<span data-ttu-id="022a6-124">Visual Studio で、**[ヘルプ]、[Microsoft Visual Studio のバージョン情報]** コマンドを使用して、**[NuGet パッケージ マネージャー]** の横に表示されるバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="022a6-124">In Visual Studio, use the **Help > About Microsoft Visual Studio** command and look at the version displayed next to **NuGet Package Manager**.</span></span>

<span data-ttu-id="022a6-125">または、パッケージ マネージャー コンソールを起動 (**[ツール]、[NuGet パッケージ マネージャー]、[パッケージ マネージャー コンソール]** の順に選択) し、「`$host`」と入力して、バージョンを含む NuGet に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="022a6-125">Alternatively, launch the Package Manager Console (**Tools > NuGet Package Manager > Package Manager Console**) and enter `$host` to see information about NuGet including the version.</span></span>

<span data-ttu-id="022a6-126">**NuGet ではどのようなプログラミング言語がサポートされますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-126">**What programming languages are supported by NuGet?**</span></span>

<span data-ttu-id="022a6-127">通常、NuGet は .NET 言語に対して動作し、プロジェクトに .NET ライブラリを取り込むように設計されています。</span><span class="sxs-lookup"><span data-stu-id="022a6-127">NuGet generally works for .NET languages and is designed to bring .NET libraries into a project.</span></span> <span data-ttu-id="022a6-128">また、いくつかのプロジェクトの種類で MSBuild と Visual Studio オートメーションがサポートされるため、程度の差はありますが他のプロジェクトと言語もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="022a6-128">Because it also supports MSBuild and Visual Studio automation in some project types, it also supports other projects and languages to various degrees.</span></span>

<span data-ttu-id="022a6-129">最新バージョンの NuGet では C#、Visual Basic、F#、WiX、C++ がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="022a6-129">The most recent version of NuGet supports C#, Visual Basic, F#, WiX, and C++.</span></span>

<span data-ttu-id="022a6-130">**NuGet ではどのようなプロジェクト テンプレートがサポートされますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-130">**What project templates are supported by NuGet?**</span></span>

<span data-ttu-id="022a6-131">NuGet では、Windows、Web、クラウド、SharePoint、Wix などのさまざまなプロジェクト テンプレートが完全にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="022a6-131">NuGet has full support for a variety of project templates like Windows, Web, Cloud, SharePoint, Wix, and so on.</span></span>

<span data-ttu-id="022a6-132">**Visual Studio テンプレートの一部であるパッケージはどのように更新すればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-132">**How do I update packages that are part of Visual Studio templates?**</span></span>

<span data-ttu-id="022a6-133">パッケージ マネージャー UI の **[更新]** タブに移動して、**[すべて更新]** を選択するか、パッケージ マネージャー コンソールで [`Update-Package` コマンド](../reference/ps-reference/ps-ref-update-package.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="022a6-133">Go to the **Updates** tab in the Package Manager UI and select **Update All**, or use the [`Update-Package` command](../reference/ps-reference/ps-ref-update-package.md) from the Package Manager Console.</span></span>

<span data-ttu-id="022a6-134">テンプレート自体を更新するには、テンプレート リポジトリを手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="022a6-134">To update the template itself, you need to manually update the template repository.</span></span> <span data-ttu-id="022a6-135">これについては、[Xavier Decoster のブログ](http://www.xavierdecoster.com/update-project-template-to-latest-nuget-packages)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-135">See [Xavier Decoster's blog](http://www.xavierdecoster.com/update-project-template-to-latest-nuget-packages) on this subject.</span></span> <span data-ttu-id="022a6-136">最新バージョンのすべての依存関係が相互に互換性がない場合、手動で更新するとテンプレートが壊れる可能性があるため、これは自身の責任で行うことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-136">Note that this is done at your own risk, because manual updates might corrupt the template if the latest version of all dependencies are not compatible with each other.</span></span>

<span data-ttu-id="022a6-137">**Visual Studio 外部で NuGet を使用できますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-137">**Can I use NuGet outside of Visual Studio?**</span></span>

<span data-ttu-id="022a6-138">はい。NuGet はコマンド ラインから直接動作します。</span><span class="sxs-lookup"><span data-stu-id="022a6-138">Yes, NuGet works directly from the command line.</span></span> <span data-ttu-id="022a6-139">[インストール ガイド](../install-nuget-client-tools.md)と [CLI 参照](../reference/nuget-exe-cli-reference.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-139">See the [Install guide](../install-nuget-client-tools.md) and the [CLI reference](../reference/nuget-exe-cli-reference.md).</span></span>

## <a name="nuget-command-line"></a><span data-ttu-id="022a6-140">NuGet コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="022a6-140">NuGet command line</span></span>

<span data-ttu-id="022a6-141">**最新バージョンの NuGet コマンド ライン ツールはどのように取得すればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-141">**How do I get the latest version of NuGet command line tool?**</span></span>

<span data-ttu-id="022a6-142">[インストール ガイド](../install-nuget-client-tools.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-142">See the [Install guide](../install-nuget-client-tools.md).</span></span> <span data-ttu-id="022a6-143">現在インストールされているツールのバージョンを確認するには、`nuget help` を使用します。</span><span class="sxs-lookup"><span data-stu-id="022a6-143">To check the current installed version of the tool, use `nuget help`.</span></span>

<span data-ttu-id="022a6-144">**nuget.exe のライセンスとは何ですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-144">**What is the license for nuget.exe?**</span></span>

<span data-ttu-id="022a6-145">MIT ライセンスの条件に従って、nuget.exe を再配布できます。</span><span class="sxs-lookup"><span data-stu-id="022a6-145">You are allowed to redistribute nuget.exe under the terms of the MIT license.</span></span> <span data-ttu-id="022a6-146">再配布を選択した nuget.exe のコピーを更新および修正するのは、お客様の責任です。</span><span class="sxs-lookup"><span data-stu-id="022a6-146">You are responsible for updating and servicing any copies of nuget.exe that you choose to redistribute.</span></span>

<span data-ttu-id="022a6-147">**NuGet コマンド ライン ツールを拡張することはできますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-147">**Is it possible to extend the NuGet command line tool?**</span></span>

<span data-ttu-id="022a6-148">はい。[Rob Reynold の投稿](http://geekswithblogs.net/robz/archive/2011/07/15/extend-nuget-command-line.aspx)で説明されているように、`nuget.exe` にカスタム コマンドを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="022a6-148">Yes, it's possible to add custom commands to `nuget.exe`, as described in [Rob Reynold's post](http://geekswithblogs.net/robz/archive/2011/07/15/extend-nuget-command-line.aspx).</span></span>

## <a name="nuget-package-manager-console-visual-studio-on-windows"></a><span data-ttu-id="022a6-149">NuGet パッケージ マネージャー コンソール (Windows の Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="022a6-149">NuGet Package Manager Console (Visual Studio on Windows)</span></span>

<span data-ttu-id="022a6-150">**パッケージ マネージャー コンソールでは DTE オブジェクトにどのようにアクセスするのですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-150">**How do I get access to the DTE object in the Package Manager console?**</span></span>

<span data-ttu-id="022a6-151">Visual Studio オートメーション オブジェクト モデルのトップ レベル オブジェクトは、DTE (開発ツール環境) オブジェクトと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="022a6-151">The top-level object in the Visual Studio automation object model is called the DTE (Development Tools Environment) object.</span></span> <span data-ttu-id="022a6-152">コンソールでは、`$DTE` という名前の変数を通じてこれが提供されます。</span><span class="sxs-lookup"><span data-stu-id="022a6-152">The console provides this through a variable named `$DTE`.</span></span> <span data-ttu-id="022a6-153">詳細については、Visual Studio 機能拡張ドキュメントの「[オートメーション モデルの概要](/visualstudio/extensibility/internals/automation-model-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-153">For more information, see [Automation Model Overview](/visualstudio/extensibility/internals/automation-model-overview) in the Visual Studio Extensibility documentation.</span></span>

<span data-ttu-id="022a6-154">**$DTE 変数を DTE2 型にキャストしようとしましたが、""EnvDTE.DTEClass" 型の "EnvDTE.DTEClass" 値を "EnvDTE80.DTE2" 型に変換できません" という内容のエラーが表示されました。何が問題なのでしょうか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-154">**I try to cast the $DTE variable to the type DTE2, but I get an error: Cannot convert the "EnvDTE.DTEClass" value of type "EnvDTE.DTEClass" to type "EnvDTE80.DTE2". What's wrong?**</span></span>

<span data-ttu-id="022a6-155">これは、PowerShell が COM オブジェクトと対話する方法に関する既知の問題です。</span><span class="sxs-lookup"><span data-stu-id="022a6-155">This is a known issue with how PowerShell interacts with a COM object.</span></span> <span data-ttu-id="022a6-156">以下を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="022a6-156">Try the following:</span></span>

```ps
`$dte2 = Get-Interface $dte ([EnvDTE80.DTE2])`
```

<span data-ttu-id="022a6-157">`Get-Interface` は、NuGet PowerShell ホストによって追加されたヘルパー関数です。</span><span class="sxs-lookup"><span data-stu-id="022a6-157">`Get-Interface` is a helper function added by the NuGet PowerShell host.</span></span>

## <a name="creating-and-publishing-packages"></a><span data-ttu-id="022a6-158">パッケージの作成と発行</span><span class="sxs-lookup"><span data-stu-id="022a6-158">Creating and publishing packages</span></span>

<span data-ttu-id="022a6-159">**フィードではどのように自分のパッケージをリストするのですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-159">**How do I list my package in a feed?**</span></span>

<span data-ttu-id="022a6-160">「[パッケージの作成と発行](../quickstart/create-and-publish-a-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-160">See [Creating and publishing a package](../quickstart/create-and-publish-a-package.md).</span></span>

<span data-ttu-id="022a6-161">**異なるバージョンの .NET Framework をターゲットとする複数バージョンのライブラリがあります。これをサポートする 1 つのパッケージをビルドするにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-161">**I have multiple versions of my library that target different versions of the .NET Framework. How do I build a single package that supports this?**</span></span>

<span data-ttu-id="022a6-162">[複数の .NET Framework バージョンとプロファイルのサポート](../create-packages/supporting-multiple-target-frameworks.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-162">See [Supporting Multiple .NET Framework Versions and Profiles](../create-packages/supporting-multiple-target-frameworks.md).</span></span>

<span data-ttu-id="022a6-163">**独自のリポジトリまたはフィードを設定するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-163">**How do I set up my own repository or feed?**</span></span>

<span data-ttu-id="022a6-164">[パッケージのホスティングの概要](../hosting-packages/overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-164">See the [Hosting packages overview](../hosting-packages/overview.md).</span></span>

<span data-ttu-id="022a6-165">**パッケージを自分の NuGet フィードに一括でアップロードするにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-165">**How can I upload packages to my NuGet feed in bulk?**</span></span>

<span data-ttu-id="022a6-166">「[Bulk publishing NuGet packages」](http://jeffhandley.com/archive/2012/12/13/Bulk-Publishing-NuGet-Packages.aspx) (NuGet パッケージの一括発行) (jeffhandly.com) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-166">See [Bulk publishing NuGet packages](http://jeffhandley.com/archive/2012/12/13/Bulk-Publishing-NuGet-Packages.aspx) (jeffhandly.com).</span></span>

## <a name="working-with-packages"></a><span data-ttu-id="022a6-167">パッケージの操作</span><span class="sxs-lookup"><span data-stu-id="022a6-167">Working with packages</span></span>

<span data-ttu-id="022a6-168">**プロジェクト レベルのパッケージとソリューション レベルのパッケージの違いは何ですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-168">**What is the difference between a project-level package and a solution-level package?**</span></span>

<span data-ttu-id="022a6-169">ソリューション レベルのパッケージ (NuGet 3.x+) はソリューションに 1 回だけインストールされ、ソリューション内のすべてのプロジェクトで使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="022a6-169">A solution-level package (NuGet 3.x+) is installed only once in a solution and is then available for all projects in the solution.</span></span> <span data-ttu-id="022a6-170">プロジェクト レベルのパッケージは、このパッケージを使用するプロジェクトごとにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="022a6-170">A project-level package is installed in each project that uses it.</span></span> <span data-ttu-id="022a6-171">ソリューション レベルのパッケージでは、パッケージ マネージャー コンソール内から呼び出すことができる新しいコマンドがインストールされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="022a6-171">A solution-level package might also install new commands that can be called from within the Package Manager Console.</span></span>

<span data-ttu-id="022a6-172">**インターネットに接続せずに NuGet パッケージをインストールすることはできますか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-172">**Is it possible to install NuGet packages without Internet connectivity?**</span></span>

<span data-ttu-id="022a6-173">はい。Scott Hanselman のブログ投稿「[How to access NuGet when nuget.org is down (or you're on a plane)](http://www.hanselman.com/blog/HowToAccessNuGetWhenNuGetorgIsDownOrYoureOnAPlane.aspx)」 (nuget.org がダウンしたとき (または飛行機内で) NuGet にアクセスする方法) (hanselman.com) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-173">Yes, see Scott Hanselman's Blog post [How to access NuGet when nuget.org is down (or you're on a plane)](http://www.hanselman.com/blog/HowToAccessNuGetWhenNuGetorgIsDownOrYoureOnAPlane.aspx) (hanselman.com).</span></span>

<span data-ttu-id="022a6-174">**既定のパッケージ フォルダーとは異なる場所にパッケージをインストールするにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-174">**How do I install packages in a different location from the default packages folder?**</span></span>

<span data-ttu-id="022a6-175">`nuget config -set repositoryPath=<path>` を使用して、`Nuget.Config` で [`repositoryPath`](../reference/nuget-config-file.md#config-section) を設定します。</span><span class="sxs-lookup"><span data-stu-id="022a6-175">Set the [`repositoryPath`](../reference/nuget-config-file.md#config-section) setting in `Nuget.Config` using `nuget config -set repositoryPath=<path>`.</span></span>

<span data-ttu-id="022a6-176">**NuGet パッケージ フォルダーがソース管理に追加されないようにするにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-176">**How do I avoid adding the NuGet packages folder into to source control?**</span></span>

<span data-ttu-id="022a6-177">`Nuget.Config` の [`disableSourceControlIntegration`](../reference/nuget-config-file.md#solution-section) を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="022a6-177">Set the [`disableSourceControlIntegration`](../reference/nuget-config-file.md#solution-section) in `Nuget.Config` to `true`.</span></span> <span data-ttu-id="022a6-178">このキーはソリューション レベルで動作するため、`$(Solutiondir)\.nuget\Nuget.Config` ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="022a6-178">This key works at the solution level and hence need to be added to the `$(Solutiondir)\.nuget\Nuget.Config` file.</span></span> <span data-ttu-id="022a6-179">Visual Studio からのパッケージの復元を有効にすると、このファイルは自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="022a6-179">Enabling package restore from Visual Studio creates this file automatically.</span></span>

<span data-ttu-id="022a6-180">**パッケージの復元を無効にするにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-180">**How do I turn off package restore?**</span></span>

<span data-ttu-id="022a6-181">「[パッケージの復元の有効化と無効化](../consume-packages/package-restore.md#enable-and-disable-package-restore-in-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022a6-181">See [Enabling and disabling package restore](../consume-packages/package-restore.md#enable-and-disable-package-restore-in-visual-studio).</span></span>

<span data-ttu-id="022a6-182">**リモートの依存関係があるローカル パッケージをインストールするときに、"依存関係を解決できません" という内容のエラーが表示されるのはなぜですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-182">**Why do I get an "Unable to resolve dependency error" when installing a local package with remote dependencies?**</span></span>

<span data-ttu-id="022a6-183">プロジェクトにローカル パッケージをインストールする場合は、**すべて**のソースを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="022a6-183">You need to select the **All** source when installing a local package into the project.</span></span> <span data-ttu-id="022a6-184">これにより、フィードを 1 つだけ使用するのではなく、すべて集約することになります。</span><span class="sxs-lookup"><span data-stu-id="022a6-184">This aggregates all the feeds instead of using just one.</span></span> <span data-ttu-id="022a6-185">このエラーが表示されるのは、ローカル リポジトリのユーザーは、多くの場合、企業ポリシーにより、リモート パッケージが誤ってインストールされないようにする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="022a6-185">The reason this error appears is that users of a local repository often want to avoid accidentally installing a remote package due to corporate polices.</span></span>

<span data-ttu-id="022a6-186">**同じフォルダーに複数のプロジェクトがあります。プロジェクトごとに別個の packages.config ファイルを使用するにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-186">**I have multiple projects in the same folder, how can I use separate packages.config files for each project?**</span></span>

<span data-ttu-id="022a6-187">別個のプロジェクトが別個のフォルダーに存在するほとんどのプロジェクトでは、NuGet で各プロジェクトの `packages.config` ファイルが特定されるため、これは問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="022a6-187">In most projects where separate projects live in separate folders, this is not a problem as NuGet identifies the `packages.config` files in each project.</span></span> <span data-ttu-id="022a6-188">NuGet 3.3+ では、同じフォルダーに複数のプロジェクトがある場合、プロジェクトの名前を `packages.config` ファイル名に挿入できます (パターン `packages.{project-name}.config` を使用)。NuGet はそのファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="022a6-188">With NuGet 3.3+ and multiple projects in the same folder, you can insert the name of the project into the `packages.config` filenames use the pattern `packages.{project-name}.config`, and NuGet uses that file.</span></span>

<span data-ttu-id="022a6-189">各プロジェクト ファイルには独自の依存関係リストが含まれるため、PackageReference を使用する場合、これは問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="022a6-189">This is not an issue when using PackageReference, as each project file contains its own list of dependencies.</span></span>

<span data-ttu-id="022a6-190">**自分のリポジトリ リストに nuget.org が表示されません。これを戻すにはどうすればよいですか?**</span><span class="sxs-lookup"><span data-stu-id="022a6-190">**I don't see nuget.org in my list of repositories, how do I get it back?**</span></span>

- <span data-ttu-id="022a6-191">自分のソース リストに `https://api.nuget.org/v3/index.json` を追加します。または、</span><span class="sxs-lookup"><span data-stu-id="022a6-191">Add `https://api.nuget.org/v3/index.json` to your list of sources, or</span></span>
- <span data-ttu-id="022a6-192">`%appdata%\.nuget\NuGet.Config` (Windows) または `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) を削除し、NuGet で自動的に再作成します。</span><span class="sxs-lookup"><span data-stu-id="022a6-192">Delete `%appdata%\.nuget\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) and let NuGet re-create it.</span></span>
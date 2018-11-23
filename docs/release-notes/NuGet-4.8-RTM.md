---
title: NuGet 4.8 RTM リリース ノート
description: NuGet 4.8.1 のリリース ノートです。既知の問題、バグ修正、追加機能、および DCR について示します。
author: karann-msft
ms.author: karann
ms.date: 5/14/2018
ms.topic: conceptual
ms.openlocfilehash: 641304059c90e360fae4d0956d7b922e34bc6501
ms.sourcegitcommit: 09107c5092050f44a0c6abdfb21db73878f78bd0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2018
ms.locfileid: "50981120"
---
# <a name="nuget-48-rtm-release-notes"></a><span data-ttu-id="5f9af-103">NuGet 4.8 RTM リリース ノート</span><span class="sxs-lookup"><span data-stu-id="5f9af-103">NuGet 4.8 RTM Release Notes</span></span>

<span data-ttu-id="5f9af-104">[Visual Studio 2017 15.8 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) には、NuGet 4.8 機能が付属しています。</span><span class="sxs-lookup"><span data-stu-id="5f9af-104">[Visual Studio 2017 15.8 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) comes with NuGet 4.8 functionality.</span></span>


<span data-ttu-id="5f9af-105">また、次の同一機能のコマンド ライン バージョンが利用可能です。</span><span class="sxs-lookup"><span data-stu-id="5f9af-105">Command line versions of the same functionality are also available:</span></span>
* <span data-ttu-id="5f9af-106">NuGet.exe 4.8 - [nuget.org/downloads](https://nuget.org/downloads)</span><span class="sxs-lookup"><span data-stu-id="5f9af-106">NuGet.exe 4.8 - [nuget.org/downloads](https://nuget.org/downloads)</span></span>
* <span data-ttu-id="5f9af-107">DotNet.exe - [.NET Core SDK 2.1.400](https://www.microsoft.com/net/download/visual-studio-sdks)</span><span class="sxs-lookup"><span data-stu-id="5f9af-107">DotNet.exe - [.NET Core SDK 2.1.400](https://www.microsoft.com/net/download/visual-studio-sdks)</span></span>


## <a name="summary-whats-new-in-this-release"></a><span data-ttu-id="5f9af-108">概要: このリリースの新機能</span><span class="sxs-lookup"><span data-stu-id="5f9af-108">Summary: What's New in this Release</span></span>
* <span data-ttu-id="5f9af-109">NuGet.exe では、Windows 10 上での長いファイル名がサポートされるようになりました。[#6937](https://github.com/NuGet/Home/issues/6937)</span><span class="sxs-lookup"><span data-stu-id="5f9af-109">NuGet.exe now supports longfilenames on Windows 10 - [#6937](https://github.com/NuGet/Home/issues/6937)</span></span>
* <span data-ttu-id="5f9af-110">クロス プラットフォームなど、MsBuild、DotNet.exe、NuGet.exe、および Visual Studio にわたって、認証プラグインが機能するようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f9af-110">Authenication plugins now work across MsBuild, DotNet.exe, NuGet.exe and Visual Studio, including cross platform.</span></span> <span data-ttu-id="5f9af-111">最初の世代の認証プラグインは、MsBuild、DotNet.exe ではサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="5f9af-111">The first generation of authentication plugins were not supported in MsBuild, DotNet.exe.</span></span> <span data-ttu-id="5f9af-112">注: VS 2017 15.9 プレビューのビルドには、VSTS 認証プラグインが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="5f9af-112">Note: VS 2017 15.9 Preview builds have a VSTS authentication plugin included.</span></span> [<span data-ttu-id="5f9af-113">#6486</span><span class="sxs-lookup"><span data-stu-id="5f9af-113">#6486</span></span>](https://github.com/NuGet/Home/issues/6486)
* <span data-ttu-id="5f9af-114">MsBuild の SDK リゾルバーは、NuGet の一部としてビルドされ、VS 対応の NuGet ツールと共にインストールを行います。</span><span class="sxs-lookup"><span data-stu-id="5f9af-114">MsBuild's SDK Resolver now builds as part of NuGet and installs with NuGet tools for VS.</span></span> <span data-ttu-id="5f9af-115">これにより、複数のバージョンでの同期の取得を防止します。[#6799](https://github.com/NuGet/Home/issues/6799)</span><span class="sxs-lookup"><span data-stu-id="5f9af-115">This will avoid versions getting out sync. [#6799](https://github.com/NuGet/Home/issues/6799)</span></span>
* <span data-ttu-id="5f9af-116">PackageReference では、DevelopmentDependency メタデータがサポートされるようになりました。[#4125](https://github.com/NuGet/Home/issues/4125)</span><span class="sxs-lookup"><span data-stu-id="5f9af-116">PackageReference now supports DevelopmentDependency metadata - [#4125](https://github.com/NuGet/Home/issues/4125)</span></span>

## <a name="known-issues"></a><span data-ttu-id="5f9af-117">既知の問題</span><span class="sxs-lookup"><span data-stu-id="5f9af-117">Known issues</span></span>
### <a name="installing-signed-packages-on-a-ci-machine-or-in-an-offline-environment-takes-longer-than-usual"></a><span data-ttu-id="5f9af-118">CI マシン上またはオフライン環境に署名済みパッケージをインストールすると、通常よりも長い時間がかかる。</span><span class="sxs-lookup"><span data-stu-id="5f9af-118">Installing signed packages on a CI machine or in an offline environment takes longer than usual</span></span>

#### <a name="issue"></a><span data-ttu-id="5f9af-119">懸案事項</span><span class="sxs-lookup"><span data-stu-id="5f9af-119">Issue</span></span>
<span data-ttu-id="5f9af-120">マシンのインターネット アクセスが制限されている場合 (CI/CD シナリオでのビルド マシンなど)、失効サーバーには到達できないため、署名済みの nuget パッケージからの警告 ([NU3028](https://docs.microsoft.com/en-us/nuget/reference/errors-and-warnings/nu3028)) が発生します。</span><span class="sxs-lookup"><span data-stu-id="5f9af-120">If the machine has restricted internet access (such as a build machine in a CI/CD scenario), installing/restoring a signed nuget package will result a warning ([NU3028](https://docs.microsoft.com/en-us/nuget/reference/errors-and-warnings/nu3028)) since the revocation servers are not reachable.</span></span> <span data-ttu-id="5f9af-121">これは想定されている動作です。</span><span class="sxs-lookup"><span data-stu-id="5f9af-121">This is expected.</span></span> <span data-ttu-id="5f9af-122">ただし、場合によっては、これによって通常よりも時間がかるパッケージのインストール/復元など、意図しない結果を引き起こす場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f9af-122">However, in some cases, this may have unintended concequences such as the package install/restore taking longer than usual.</span></span>

#### <a name="workaround"></a><span data-ttu-id="5f9af-123">回避策</span><span class="sxs-lookup"><span data-stu-id="5f9af-123">Workaround</span></span>
<span data-ttu-id="5f9af-124">失効チェック モードを切り替えるために環境変数を導入した Visual Studio 15.8.4 および NuGet.exe 4.8.1 に更新します。</span><span class="sxs-lookup"><span data-stu-id="5f9af-124">Update to Visual Studio 15.8.4 and NuGet.exe 4.8.1 where we introduced an environment variable to switch the revocation check mode.</span></span>
<span data-ttu-id="5f9af-125">`NUGET_CERT_REVOCATION_MODE` 環境変数を `offline` に設定すると、NuGet は、キャッシュされた証明書失効リストに対してのみ証明書の失効ステータスをチェックするように設定され、NuGet は失効サーバーへのアクセスを試行しなくなります。</span><span class="sxs-lookup"><span data-stu-id="5f9af-125">Setting the `NUGET_CERT_REVOCATION_MODE` environment variable to `offline` will force NuGet to check the revocation status of the certificate only against the cached certificate revocation list, and NuGet will not attempt to reach revocation servers.</span></span> <span data-ttu-id="5f9af-126">失効チェック モードが `offline` に設定された場合、警告は情報へとダウングレードされます。</span><span class="sxs-lookup"><span data-stu-id="5f9af-126">When the revocation check mode is set to `offline`, the warning will be downgraded to an info.</span></span>

> [!Warning]
> <span data-ttu-id="5f9af-127">通常の状況では、失効チェック モードをオフラインに切り替えることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="5f9af-127">It is not recommended to switch the revocation check mode to offline under normal cirumstances.</span></span> <span data-ttu-id="5f9af-128">オフラインに切り替えると、NuGet はオンライン失効チェックをスキップして、キャッシュされた証明書失効リスト (期限切れの場合もある) に対するオフライン失効チェックのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f9af-128">Doing so will cause NuGet to skip online revocation check and perform only an offline revocation check against the cached certificate revocation list which may be out of date.</span></span> <span data-ttu-id="5f9af-129">これは、証明書の署名が失効済みになった可能性のあるパッケージが、引き続きインストール/復元されることを意味します。オフラインに切り替えなければ、失効チェックでエラーになり、インストールされなかったはずのパッケージです。</span><span class="sxs-lookup"><span data-stu-id="5f9af-129">This means packages where the signing certificate may have been revoked, will continue to be installed/restored, which otherwise would have failed revocation check and would not have been installed.</span></span>

### <a name="the-migrate-packagesconfig-to-packagereference-option-is-not-available-in-the-right-click-context-menu"></a><span data-ttu-id="5f9af-130">右クリックのコンテキスト メニューで `Migrate packages.config to PackageReference...` オプションを使用できない</span><span class="sxs-lookup"><span data-stu-id="5f9af-130">The `Migrate packages.config to PackageReference...` option is not available in the right-click context menu</span></span>

#### <a name="issue"></a><span data-ttu-id="5f9af-131">懸案事項</span><span class="sxs-lookup"><span data-stu-id="5f9af-131">Issue</span></span>

<span data-ttu-id="5f9af-132">プロジェクトを最初に開いたとき、NuGet 操作を行うまで NuGet が初期化されていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5f9af-132">When a project is first opened, NuGet may not have initialized until a NuGet operation is performed.</span></span> <span data-ttu-id="5f9af-133">これにより、`packages.config` または `References` 上の右クリックのコンテキスト メニューで、移行オプションが表示されません。</span><span class="sxs-lookup"><span data-stu-id="5f9af-133">This causes the migration option to not show up in the right-click context menu on `packages.config` or `References`.</span></span>

#### <a name="workaround"></a><span data-ttu-id="5f9af-134">回避策</span><span class="sxs-lookup"><span data-stu-id="5f9af-134">Workaround</span></span>

<span data-ttu-id="5f9af-135">次の NuGet アクションのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f9af-135">Perform any one of the following NuGet actions:</span></span>
* <span data-ttu-id="5f9af-136">パッケージ マネージャー UI を開く - `References` を右クリックし、`Manage NuGet Packages...` を選択する</span><span class="sxs-lookup"><span data-stu-id="5f9af-136">Open the Package Manager UI - Right-click on `References` and select `Manage NuGet Packages...`</span></span>
* <span data-ttu-id="5f9af-137">パッケージ マネージャー コンソールを開く - `Tools > NuGet Package Manager` から、`Package Manager Console` を選択する</span><span class="sxs-lookup"><span data-stu-id="5f9af-137">Open the Package Manager Console - From `Tools > NuGet Package Manager`, select `Package Manager Console`</span></span>
* <span data-ttu-id="5f9af-138">NuGet 復元を実行する - ソリューション エクスプローラーのソリューション ノードを右クリックし、`Restore NuGet Packages` を選択する</span><span class="sxs-lookup"><span data-stu-id="5f9af-138">Run NuGet restore - Right-click on the solution node in the Solution Explorer and select `Restore NuGet Packages`</span></span>
* <span data-ttu-id="5f9af-139">NuGet 復元もトリガーするプロジェクトをビルドする</span><span class="sxs-lookup"><span data-stu-id="5f9af-139">Build the project which also triggers NuGet restore</span></span>

<span data-ttu-id="5f9af-140">これで、移行オプションを表示できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5f9af-140">You should now be able to see the migration option.</span></span> <span data-ttu-id="5f9af-141">このオプションは ASP.NET と C++ のプロジェクト タイプではサポートされておらず、表示されません。</span><span class="sxs-lookup"><span data-stu-id="5f9af-141">Note that this option is not supported and will not show up for ASP.NET and C++ project types.</span></span>
<span data-ttu-id="5f9af-142">注: これは VS 2017 15.9 プレビュー 3 で修正されました。</span><span class="sxs-lookup"><span data-stu-id="5f9af-142">Note: This has been fixed in VS 2017 15.9 Preview 3</span></span>

## <a name="issues-fixed-in-this-release"></a><span data-ttu-id="5f9af-143">このリリースで修正された問題</span><span class="sxs-lookup"><span data-stu-id="5f9af-143">Issues fixed in this release</span></span>

### <a name="bugs"></a><span data-ttu-id="5f9af-144">バグ</span><span class="sxs-lookup"><span data-stu-id="5f9af-144">Bugs</span></span>
#### <a name="signing"></a><span data-ttu-id="5f9af-145">署名</span><span class="sxs-lookup"><span data-stu-id="5f9af-145">Signing</span></span>
* <span data-ttu-id="5f9af-146">署名: 署名済みパッケージのオフライン環境でのインストール [#7008](https://github.com/NuGet/Home/issues/7008) -- 4.8.1 で修正済み</span><span class="sxs-lookup"><span data-stu-id="5f9af-146">Signing: Installing signed package in offline environment [#7008](https://github.com/NuGet/Home/issues/7008) -- Fixed in 4.8.1</span></span>
* <span data-ttu-id="5f9af-147">署名: 不正な URL チェック - [#7174](https://github.com/NuGet/Home/issues/7174)</span><span class="sxs-lookup"><span data-stu-id="5f9af-147">Signing:  incorrect URL check - [#7174](https://github.com/NuGet/Home/issues/7174)</span></span>
* <span data-ttu-id="5f9af-148">署名: パッケージにリポジトリの副署名がある場合に、RepositorySignatureVerifier でパッケージの整合性をチェックする - [#6926](https://github.com/NuGet/Home/issues/6926)</span><span class="sxs-lookup"><span data-stu-id="5f9af-148">Signing:  check package integrity in RepositorySignatureVerifier when package is repository countersigned - [#6926](https://github.com/NuGet/Home/issues/6926)</span></span>
* <span data-ttu-id="5f9af-149">"パッケージの整合性チェックに失敗しました。"</span><span class="sxs-lookup"><span data-stu-id="5f9af-149">"Package Integrity check failed."</span></span> <span data-ttu-id="5f9af-150">のメッセージに、パッケージ ID (およびエラー コード) が必要である - [#6944](https://github.com/NuGet/Home/issues/6944)</span><span class="sxs-lookup"><span data-stu-id="5f9af-150">should have package ID in message (and error code) - [#6944](https://github.com/NuGet/Home/issues/6944)</span></span>
* <span data-ttu-id="5f9af-151">リポジトリの署名済みパッケージの検証によって、別の証明書で署名されたパッケージを許可する - [#6884](https://github.com/NuGet/Home/issues/6884)</span><span class="sxs-lookup"><span data-stu-id="5f9af-151">Repository signed package verification allows packages signed by different certificate - [#6884](https://github.com/NuGet/Home/issues/6884)</span></span>
* <span data-ttu-id="5f9af-152">NuGet - 署名 - タイムスタンプ URL を https:// にできない。</span><span class="sxs-lookup"><span data-stu-id="5f9af-152">NuGet - Signing - Timestamp URL can not be https:// ?</span></span><span data-ttu-id="5f9af-153"> - [#6871](https://github.com/NuGet/Home/issues/6871)</span><span class="sxs-lookup"><span data-stu-id="5f9af-153"> - [#6871](https://github.com/NuGet/Home/issues/6871)</span></span>
* <span data-ttu-id="5f9af-154">NuSpec パッキングのシナリオで NullRef しない。また、オプションを改善。 - [#6866](https://github.com/NuGet/Home/issues/6866)</span><span class="sxs-lookup"><span data-stu-id="5f9af-154">Don't NullRef in NuSpec packing scenario, also improve options - [#6866](https://github.com/NuGet/Home/issues/6866)</span></span>
* <span data-ttu-id="5f9af-155">副署名にタイムスタンプを追加するとき、署名者情報の更新中はメモリが無効になる - [#6840](https://github.com/NuGet/Home/issues/6840)</span><span class="sxs-lookup"><span data-stu-id="5f9af-155">Memory is invalid while updating signer info when adding timestamp to countersignature - [#6840](https://github.com/NuGet/Home/issues/6840)</span></span>
* <span data-ttu-id="5f9af-156">署名: CTL 例外を削除する - [#6794](https://github.com/NuGet/Home/issues/6794)</span><span class="sxs-lookup"><span data-stu-id="5f9af-156">Signing:  remove CTL exceptions - [#6794](https://github.com/NuGet/Home/issues/6794)</span></span>
* <span data-ttu-id="5f9af-157">署名:  contentUrl が必ず HTTPS になる - [#6777](https://github.com/NuGet/Home/issues/6777)</span><span class="sxs-lookup"><span data-stu-id="5f9af-157">Signing:  contentUrl MUST be HTTPS - [#6777](https://github.com/NuGet/Home/issues/6777)</span></span>
* <span data-ttu-id="5f9af-158">署名: SignedPackageVerifierSettings.VSClientDefaultPolicy が使用されない - [#6601](https://github.com/NuGet/Home/issues/6601)</span><span class="sxs-lookup"><span data-stu-id="5f9af-158">Signing:  SignedPackageVerifierSettings.VSClientDefaultPolicy is unused - [#6601](https://github.com/NuGet/Home/issues/6601)</span></span>


#### <a name="pack"></a><span data-ttu-id="5f9af-159">パック</span><span class="sxs-lookup"><span data-stu-id="5f9af-159">Pack</span></span>
* <span data-ttu-id="5f9af-160">nuspec のパックに dotnet.exe を使用している場合、復元およびビルドが必須ではいけない - [#6866](https://github.com/NuGet/Home/issues/6866)</span><span class="sxs-lookup"><span data-stu-id="5f9af-160">restore and build should not be needed when using dotnet.exe to pack nuspec - [#6866](https://github.com/NuGet/Home/issues/6866)</span></span>
* <span data-ttu-id="5f9af-161">NuspecProperties で空の置換トークンが許可される  - [#6722](https://github.com/NuGet/Home/issues/6722)</span><span class="sxs-lookup"><span data-stu-id="5f9af-161">Allow empty replacement tokens in NuspecProperties  - [#6722](https://github.com/NuGet/Home/issues/6722)</span></span>
* <span data-ttu-id="5f9af-162">NuspecProperties が指定された場合に、PackTask が NullReferenceException をスローする - [#4649](https://github.com/NuGet/Home/issues/4649)</span><span class="sxs-lookup"><span data-stu-id="5f9af-162">PackTask throws NullReferenceException when NuspecProperties is specified - [#4649](https://github.com/NuGet/Home/issues/4649)</span></span>

#### <a name="accessibility"></a><span data-ttu-id="5f9af-163">ユーザー補助</span><span class="sxs-lookup"><span data-stu-id="5f9af-163">Accessibility</span></span>
* <span data-ttu-id="5f9af-164">ユーザー補助: PM UI で、パッケージ ボタン下にある 'プレリリース' という文字列が、そのパッケージの説明で隠れてしまう - [#4504](https://github.com/NuGet/Home/issues/4504)</span><span class="sxs-lookup"><span data-stu-id="5f9af-164">[Accessibility] String ‘Prerelease’ under package button is covered by its package description in PM UI - [#4504](https://github.com/NuGet/Home/issues/4504)</span></span>
* <span data-ttu-id="5f9af-165">ユーザー補助: PM UI で、'Microsoft Visual Studio Offline Packages' を選択すると、パッケージ ソースのドロップ ダウンと設定ボタンの表示が切れてしまう- [#4502](https://github.com/NuGet/Home/issues/4502)</span><span class="sxs-lookup"><span data-stu-id="5f9af-165">[Accessibility] Package source drop down and settings button truncated when selecting ‘Microsoft Visual Studio Offline Packages’ in PM UI - [#4502](https://github.com/NuGet/Home/issues/4502)</span></span>

#### <a name="powershell-management-console-pmc"></a><span data-ttu-id="5f9af-166">Powershell 管理コンソール (PMC)</span><span class="sxs-lookup"><span data-stu-id="5f9af-166">Powershell Management Console (PMC)</span></span>
* <span data-ttu-id="5f9af-167">`Update-Package` で、PackageReference バージョンの範囲が無視される - [#6775](https://github.com/NuGet/Home/issues/6775)</span><span class="sxs-lookup"><span data-stu-id="5f9af-167">`Update-Package` ignores PackageReference version range - [#6775](https://github.com/NuGet/Home/issues/6775)</span></span>
* <span data-ttu-id="5f9af-168">`Update-Package -reinstall` のソリューション全体の問題 - [#3127](https://github.com/NuGet/Home/issues/3127)</span><span class="sxs-lookup"><span data-stu-id="5f9af-168">`Update-Package -reinstall` solution wide issue - [#3127](https://github.com/NuGet/Home/issues/3127)</span></span>
* <span data-ttu-id="5f9af-169">`Update-Package [packagename] -reinstall` で、名前が指定されたパッケージ単独ではなく、すべてのパッケージが再インストールされる - [#737](https://github.com/NuGet/Home/issues/737)</span><span class="sxs-lookup"><span data-stu-id="5f9af-169">`Update-Package [packagename] -reinstall` reinstalls all packages instead of just the named one - [#737](https://github.com/NuGet/Home/issues/737)</span></span>
* <span data-ttu-id="5f9af-170">パッケージ マネージャー コンソールから、一覧に記載されていない NuGet パッケージに対する更新が可能 - [#4553](https://github.com/NuGet/Home/issues/4553)</span><span class="sxs-lookup"><span data-stu-id="5f9af-170">Can update to unlisted NuGet package from the Package Manager Console - [#4553](https://github.com/NuGet/Home/issues/4553)</span></span>

#### <a name="misc"></a><span data-ttu-id="5f9af-171">[その他]</span><span class="sxs-lookup"><span data-stu-id="5f9af-171">Misc</span></span>
* <span data-ttu-id="5f9af-172">`NuGet update self` を修正するために、NuGet.Commandline nupkg を semver2.0 にできない - [#7116](https://github.com/NuGet/Home/issues/7116)</span><span class="sxs-lookup"><span data-stu-id="5f9af-172">To fix `NuGet update self` NuGet.Commandline nupkg should not be semver2.0 - [#7116](https://github.com/NuGet/Home/issues/7116)</span></span>
* <span data-ttu-id="5f9af-173">NU1107 インストール エラーでのエクスペリエンスの向上 - [#7107](https://github.com/NuGet/Home/issues/7107)</span><span class="sxs-lookup"><span data-stu-id="5f9af-173">Improve experiences with NU1107 install failures - [#7107](https://github.com/NuGet/Home/issues/7107)</span></span>
* <span data-ttu-id="5f9af-174">GetAuthenticationCredentialRequest のシリアル化が正しくない - [#6983](https://github.com/NuGet/Home/issues/6983)</span><span class="sxs-lookup"><span data-stu-id="5f9af-174">The serialization of GetAuthenticationCredentialRequest is incorrect - [#6983](https://github.com/NuGet/Home/issues/6983)</span></span>
* <span data-ttu-id="5f9af-175">UI スレッド以外で初期化された場合、NuGet Visual Studio AsyncPackage が読み込めない - [#6976](https://github.com/NuGet/Home/issues/6976)</span><span class="sxs-lookup"><span data-stu-id="5f9af-175">NuGet Visual Studio AsyncPackage fails to load when initialized off the UI thread - [#6976](https://github.com/NuGet/Home/issues/6976)</span></span>
* <span data-ttu-id="5f9af-176">復元において、project.json が必要であることを示す誤ったエラーが報告される - [#6959](https://github.com/NuGet/Home/issues/6959)</span><span class="sxs-lookup"><span data-stu-id="5f9af-176">Restore is reporting misleading errors stating project.json is needed - [#6959](https://github.com/NuGet/Home/issues/6959)</span></span>
* <span data-ttu-id="5f9af-177">パッケージ マネージャー UI : 変更のプレビューで、[OK] ボタンがキーボードから自動的に使用できない - [#6893](https://github.com/NuGet/Home/issues/6893)</span><span class="sxs-lookup"><span data-stu-id="5f9af-177">Package manager UI : preview changes, ok button not automatically useable by keyboard - [#6893](https://github.com/NuGet/Home/issues/6893)</span></span>
* <span data-ttu-id="5f9af-178">p2p リファレンスのあるプロジェクトで、RestoreSources が無視される - [#6776](https://github.com/NuGet/Home/issues/6776)</span><span class="sxs-lookup"><span data-stu-id="5f9af-178">RestoreSources are ignored for project with p2p references - [#6776](https://github.com/NuGet/Home/issues/6776)</span></span>
* <span data-ttu-id="5f9af-179">.NET Framework テンプレートを使用して単体テスト プロジェクトを作成すると、packages.config を使ったより古いプロジェクト モデルが開かれる - [#6736](https://github.com/NuGet/Home/issues/6736)</span><span class="sxs-lookup"><span data-stu-id="5f9af-179">Creating unit test project using .NET Framework template will open older project model with packages.config - [#6736](https://github.com/NuGet/Home/issues/6736)</span></span>
* <span data-ttu-id="5f9af-180">プロジェクト リファレンスでパッケージ依存関係を上書き可能にする - [#6536](https://github.com/NuGet/Home/issues/6536)</span><span class="sxs-lookup"><span data-stu-id="5f9af-180">allow project reference to override package dependency - [#6536](https://github.com/NuGet/Home/issues/6536)</span></span>
* <span data-ttu-id="5f9af-181">MSBuild タスクで NoDefaultExcludes を公開する - [#6450](https://github.com/NuGet/Home/issues/6450)</span><span class="sxs-lookup"><span data-stu-id="5f9af-181">Expose NoDefaultExcludes in MSBuild task - [#6450](https://github.com/NuGet/Home/issues/6450)</span></span>
* <span data-ttu-id="5f9af-182">ウィンドウ サイズを変更すると、"Clear All NuGet Cache(s)\(すべての NuGet キャッシュをクリアする\)" のステータス メッセージが表示されなくなる場合がある - [#5938](https://github.com/NuGet/Home/issues/5938)</span><span class="sxs-lookup"><span data-stu-id="5f9af-182">Status message for "Clear All NuGet Cache(s)" can be hidden on window resize - [#5938](https://github.com/NuGet/Home/issues/5938)</span></span>


[<span data-ttu-id="5f9af-183">このリリースで修正されたすべての問題一覧</span><span class="sxs-lookup"><span data-stu-id="5f9af-183">List of all issues fixed in this release</span></span>](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.8")
---
title: NuGet CLI setapikey コマンド
description: Nuget.exe setapikey コマンドのリファレンス
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 66fc62074b4e7c39ff2ed6b515eee9f821530536
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34817685"
---
# <a name="setapikey-command-nuget-cli"></a>setapikey コマンド (NuGet CLI)

**適用されます:** パッケージ消費、パブリッシング&bullet;**サポートされているバージョン:** すべて

特定のサーバー URL の API キーを保存`NuGet.Config`を後続のコマンドを入力する必要があるようにします。

## <a name="usage"></a>使用法

```cli
nuget setapikey <key> -Source <url> [options]
```

ここで`<source>`サーバーを識別しますおよび`<key>`キーまたはパスワードを保存します。 場合`<source>`は省略すると、nuget.org と見なされます。

## <a name="options"></a>オプション

| オプション | 説明 |
| --- | --- |
| ConfigFile | NuGet 構成ファイルを適用します。 指定しない場合、 `%AppData%\NuGet\NuGet.Config` (Windows) または`~/.nuget/NuGet/NuGet.Config`(Mac または Linux) を使用します。|
| ForceEnglishOutput | *(3.5 +)* インバリアント、英語ベースのカルチャを使用して実行する nuget.exe を強制します。 |
| ヘルプ | ヘルプ コマンドに関する情報を表示します。 |
| NonInteractive | ユーザー入力または確認を要求するプロンプトを抑制します。 |
| 詳細度 | 出力に表示される詳細情報の量を指定します:*通常*、 *quiet*、*詳細*です。 |

参照してください[環境変数](cli-ref-environment-variables.md)

## <a name="examples"></a>使用例

```cli
nuget setapikey 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a

nuget setapikey 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -source https://example.com/nugetfeed
```
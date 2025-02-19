---
title: GitHub Codespaces のドットファイルのトラブルシューティング
allowTitleToDifferFromFilename: true
intro: 一般的なドットファイル issue のトラブルシューティング手順。
product: '{% data reusables.gated-features.codespaces %}'
versions:
  fpt: '*'
  ghec: '*'
type: reference
topics:
  - Codespaces
shortTitle: Dotfiles
ms.openlocfilehash: c316909f66d88b0f4f1fe52d6740af9b1e0d4854
ms.sourcegitcommit: f638d569cd4f0dd6d0fb967818267992c0499110
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2022
ms.locfileid: '148109283'
---
Codespace によるドットファイルからの構成設定の取得が失敗した場合は、次のデバッグ手順を実行する必要があります。

1. [個人の {% data variables.product.prodname_github_codespaces %} 設定](https://github.com/settings/codespaces)で **[ドットファイルを自動的にインストールする]** を選んで、ドットファイルを有効にします。

   ![[Automatically install dotfiles]\(ドットファイルを自動的にインストールする\) オプション](/assets/images/help/codespaces/automatically-install-dotfiles.png)

1. ドットファイルが複製されているかどうかを確認するには、`/workspaces/.codespaces/.persistedshare/dotfiles` をチェックしてください。
   - ドットファイルが複製されている場合は、インストール スクリプトを手動で再実行して、それが実行可能であることを確認してください。
   - ドットファイルが複製されていない場合は、複製で問題が発生していたかどうかを確認するために、`/workspaces/.codespaces/.persistedshare/EnvironmentLog.txt` をチェックしてください。
1. 考えられる問題について、`/workspaces/.codespaces/.persistedshare/creation.log` をチェックしてください。 詳細については、「[作成ログ](/codespaces/troubleshooting/codespaces-logs#creation-logs)」を参照してください。

ドットファイルの構成が正常に取得されたものの、構成の一部に codespace との互換性がない場合は、`$CODESPACES` 環境変数を使用して、codespace 固有の構成設定の条件付きロジックを追加します。

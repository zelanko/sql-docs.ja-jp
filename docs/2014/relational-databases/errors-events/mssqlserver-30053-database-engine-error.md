---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b53e86df555ea5e9e9abc3e3afbf959dde74e0b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551857"
---
# <a name="mssqlserver_30053"></a>MSSQLSERVER_30053
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|30053|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|FTXT_QUERY_E_WORDBREAKINGTIMEOUT|  
|メッセージ テキスト|フルテキスト クエリ文字列の単語区切り処理がタイムアウトしました。 このタイムアウトは、ワード ブレーカーによるフルテキスト クエリ文字列の処理が長時間かかったか、サーバー上で実行されているクエリ数が多い場合に発生する可能性があります。 負荷を少なくしてクエリの再実行を試みてください。|  
  
## <a name="explanation"></a>説明  
 単語区切りのタイムアウト エラーは、次の状況で発生する可能性があります。  
  
-   クエリ言語のワード ブレーカーが正しく構成されていない場合。たとえば、レジストリ設定が正しくない場合です。  
  
-   ワード ブレーカーが特定のクエリ文字列に対して誤動作する。  
  
-   ワード ブレーカーが特定のクエリ文字列に対して過剰なデータを返す。 過剰なデータは、バッファー オーバーラン攻撃を引き起こす可能性のあるものとして処理されます。これにより、単語区切りサービスをホストする、フィルター デーモン プロセス (fdhost.exe) がシャットダウンされます。  
  
-   フィルター デーモン プロセスの構成が正しくない。  
  
     パスワードの期限が切れている場合、またはドメイン ポリシーが原因でフィルター デーモン アカウントがログオンできない場合。この 2 つは、最も一般的な構成上の問題です。  
  
-   クエリが集中的に行われるワークロードをサーバー インスタンスで実行している場合。たとえば、ワード ブレーカーによるフルテキスト クエリ文字列の処理が長時間かかったり、多数のクエリがサーバー上で実行されている場合です。 この状況がエラーの原因になることはまれです。  
  
## <a name="user-action"></a>ユーザーの操作  
 次に示すように、タイムアウトについて考えられる原因に適した、ユーザーのアクションを選択してください。  
  
|考えられる原因|ユーザー アクション|  
|--------------------|-----------------|  
|クエリ言語のワード ブレーカーが正しく構成されていない。|サード パーティ製のワード ブレーカーを使用しているとき、ワード ブレーカーがオペレーティング システムに正しく登録されていない場合があります。 この場合は、ワード ブレーカーを再登録してください。 詳細については、「[Revert the Word Breakers Used by Search to the Previous Version](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)」(検索で使用するワード ブレーカーを以前のバージョンに戻す) を参照してください。|  
|ワード ブレーカーが特定のクエリ文字列に対して誤動作する。|ワード ブレーカーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている場合は、マイクロソフト カスタマー サポート サービスに問い合わせてください。|  
|ワード ブレーカーが特定のクエリ文字列に対して過剰なデータを返す。|ワード ブレーカーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている場合は、マイクロソフト カスタマー サポート サービスに問い合わせてください。|  
|フィルター デーモン プロセスの構成が正しくない。|正しいパスワードを使用していることと、フィルター デーモン アカウントのログオンがドメイン ポリシーによって拒否されていないことを確認してください。|  
|クエリが集中的に行われるワークロードをサーバー インスタンスで実行している。|負荷を少なくしてクエリの再実行を試みてください。|  
  
## <a name="see-also"></a>参照  
 [フルテキストフィルターデーモンランチャーのサービスアカウントの設定](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [フルテキスト検索](../search/full-text-search.md)   
 [sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [検索用のワードブレーカーとステミング機能の構成と管理](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [検索用フィルターの構成と管理](../search/configure-and-manage-filters-for-search.md)  
  
  

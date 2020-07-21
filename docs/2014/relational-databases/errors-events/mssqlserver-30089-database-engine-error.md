---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9cbf77c21b55542dac80d8d8ce376f0cc3a5e9d4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551811"
---
# <a name="mssqlserver_30089"></a>MSSQLSERVER_30089
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|30089|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|IFTS_FDHOST_TERMINATEDABNORMAL|  
|メッセージ テキスト|フルテキスト フィルター デーモン ホスト (FDHost) プロセスが異常停止しました。 この問題は、ワード ブレーカー、ステマー、フィルターなどの言語コンポーネントの不適切な構成または誤動作が原因で、フルテキスト インデックスの作成中またはクエリの処理中に回復不可能なエラーが生じた場合に発生することがあります。 プロセスは自動的に再開されます。|  
  
## <a name="explanation"></a>説明  
 何らかの問題が発生したため、フルテキスト フィルター デーモン ホストが異常停止しました。 問題の原因として、不適切な形式のドキュメント、フィルターやワード ブレーカーのバグ、フィルター デーモンの問題などが考えられます。  
  
## <a name="user-action"></a>ユーザーの操作  
 通常、デーモンはエラーから回復します。 デーモンのエラーが継続する場合は、トラブルシューティングが必要になります。 問題を切り離すために、次の操作を試みてください。  
  
1.  新しい言語コンポーネントを最近インストールした場合は、そのコンポーネントをシステムから削除します。  
  
2.  クロール ログを調べて、フルテキスト インデックスの作成に失敗した新しいドキュメントがあるか確認します。該当するドキュメントがあれば、それを削除します。  
  
## <a name="see-also"></a>参照  
 [sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [検索用のワードブレーカーとステミング機能の構成と管理](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [検索用フィルターの構成と管理](../search/configure-and-manage-filters-for-search.md)  
  
  

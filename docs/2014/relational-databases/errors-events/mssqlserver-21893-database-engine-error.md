---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8daf50aa25a21ec81531a728dfb4e05adb5de62c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553415"
---
# <a name="mssqlserver_21893"></a>MSSQLSERVER_21893
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21893|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21893|  
|メッセージ テキスト|元のパブリッシャー '%s' のサブスクライバー (%s) は、リダイレクトされたパブリッシャー '%s' でリモート サーバーとして表示されていません。 `sp_addlinkedserver`リダイレクトされたパブリッシャーでを実行して、これらのサブスクライバーをリモートサーバーとして追加します。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_redirected_publisher` は、リモート サーバーでパブリッシャー データベースのサブスクリプション メタデータ テーブルを使用して関連付けられているサブスクライバーを特定し、サブスクライバーの master.dbo.sysservers に関連付けられているエントリがあることを確認します。 このエラーは、特定されたサブスクライバーのいずれかが存在しない場合に発生します。  
  
 このエラーは重大なエラーとは見なされません。 新しいパブリッシャーで適切なサブスクライバー エントリを取得できなくてもレプリケーションに対する影響は限定的なため、このエラーが発生するとエージェントは情報としてエラーをログに記録しますが、終了することはありません。 sysservers にサブスクライバーの適切なエントリがないと、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を介して一部のサブスクリプション管理操作を実行したときに失敗する場合があります。 ただし、これらと同じ操作は、管理ストアド プロシージャを明示的に実行することによって正常に実行できます。  
  
## <a name="user-action"></a>ユーザーの操作  
 特定されたサブスクライバーのそれぞれについてリダイレクトされたパブリッシャーで `sp_addlinkedserver` を実行し、これらをリモート サーバーとして追加します。 次に、`sp_serveroption` を実行し、サーバーにサブスクライバー ビットを設定します。  
  
  

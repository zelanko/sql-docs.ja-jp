---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb1af04b56685d0e1b5a703b812d08d88909b693
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034568"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21899|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21899|  
|メッセージ テキスト|元のパブリッシャー '%s' のサブスクライバーの sysserver エントリがあるかどうかを判断するために、リダイレクトされたパブリッシャー '%s' で実行したクエリが、エラー '%d'、エラー メッセージ '%s' で失敗しました。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_redirected_publisher` は、リモート サーバーでパブリッシャー データベースのサブスクリプション メタデータ テーブルにクエリを実行し、関連付けられているサブスクライバーを特定します。 このクエリが失敗すると、エラー 21899 が返されます。 検証のクエリでは、リダイレクトされたパブリッシャーのパブリッシュされたデータベースにアクセスする必要があります。 元のパブリッシャーに対して `sp_adddistpublisher` が呼び出されたときに指定されたログインに、リダイレクトされたパブリッシャーのパブリッシュされたデータベースにアクセスするための権限がない場合、エラー 21899 が返されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 示されたエラー メッセージを確認し、エラーの原因を特定して適切な修正措置を行います。  
  
  

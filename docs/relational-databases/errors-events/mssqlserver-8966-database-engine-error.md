---
title: MSSQLSERVER_8966 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f973edb4af5d9a32d449ec98c411e883d090a253
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636959"
---
# <a name="mssqlserver_8966"></a>MSSQLSERVER_8966
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|8966|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|メッセージ テキスト|ラッチ型 TYPE のページ P_ID を読み取ってラッチすることができません。 OPERATION が失敗しました。|  
  
## <a name="explanation"></a>説明  
ページの読み取りに失敗したか、PFS ページまたは GAM ページでラッチを取得できませんでした。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに、ラッチ タイムアウトまたは他の添付メッセージが記録される場合があります。  
  
## <a name="user-action"></a>ユーザーの操作  
SQL エラー ログの添付メッセージを確認し、これらのエラーを解決します。  
  

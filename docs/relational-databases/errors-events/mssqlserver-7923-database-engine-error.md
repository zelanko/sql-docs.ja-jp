---
title: MSSQLSERVER_7923 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7923 (Database Engine error)
ms.assetid: b09a95e2-0ffe-4847-aa77-51e6639259f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ce6df367610f21801e85e36b8d9c9f698d0021dd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767937"
---
# <a name="mssqlserver_7923"></a>MSSQLSERVER_7923
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|7923|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_SUMMARY_TABLE_NAME|  
|メッセージ テキスト|テーブル TABLE、オブジェクト ID O_ID。|  
  
## <a name="explanation"></a>説明  
これは、DBCC CHECKALLOC コマンドからの情報メッセージです。 このメッセージには、テーブル内のすべてのアロケーション ユニットに関する割り当て情報の一覧が含まれており、この一覧の先頭にテーブルの名前と ID が表示されます。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  

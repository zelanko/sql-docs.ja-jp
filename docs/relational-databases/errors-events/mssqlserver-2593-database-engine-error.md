---
title: MSSQLSERVER_2593 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d8691278faf09049a7fa4f5b99f3636858baff3c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723822"
---
# <a name="mssqlserver_2593"></a>MSSQLSERVER_2593
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|2593|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_OBJECT_ROW_PAGE_SUMMARY|  
|メッセージ テキスト|オブジェクト 'OBJECT' の PAGECOUNT ページには ROWCOUNT 行あります。|  
  
## <a name="explanation"></a>説明  
このメッセージは、DBCC CHECKALLOC を除くすべての DBCC チェックから返される情報出力の一部であり、指定されたオブジェクトの行カウントおよびページ カウントを示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  

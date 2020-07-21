---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 85859dafcdaf8321adb1211be9bb51d37930331e
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552177"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2508|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|メッセージ テキスト|オブジェクト "%.\*ls"、インデックス ID %d、パーティション ID %I64d、アロケーション ユニット ID %I64d (型 %.\*ls) の %.*ls のカウントが正しくありません。 DBCC UPDATEUSAGE を実行してください。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、テーブルおよびインデックスの行やページのカウント値が正しくならないことがあります。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンで作成したデータベースはカウントが誤っている場合があります。 DBCC CHECKDB は、これらのエラーを検出するように拡張されており、エラーが見つかるとこの警告メッセージを返します。  
  
## <a name="user-action"></a>ユーザーの操作  
 指定したオブジェクトやインデックス、またはオブジェクトが格納されているデータベースに対して DBCC UPDATEUSAGE を実行し、無効なカウントを修正します。  
  
  

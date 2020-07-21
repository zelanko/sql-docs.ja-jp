---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8a94e95b6714876649664ff732323c9efc484db3
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553327"
---
# <a name="mssqlserver_7911"></a>MSSQLSERVER_7911
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7911|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|メッセージ テキスト|修復:ページ P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) から割り当て解除されました。|  
  
## <a name="explanation"></a>説明  
 単一ページ スロット配列の IAM (Index Allocation Map) ページから 1 ページが割り当て解除されたことを示す、REPAIR からの情報メッセージです。  
  
## <a name="user-action"></a>ユーザーの操作  
 なし  
  
  

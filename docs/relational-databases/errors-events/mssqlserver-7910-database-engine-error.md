---
title: MSSQLSERVER_7910 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eee9101e3d9d0684b1e2f7cbc28f99777823f33
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85793145"
---
# <a name="mssqlserver_7910"></a>MSSQLSERVER_7910
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|7910|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC2_REPAIR_PAGE_ALLOCATED|  
|メッセージ テキスト|修復:ページ P_ID が、オブジェクト ID O_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE) に割り当てられました。|  
  
## <a name="explanation"></a>説明  
単一ページ スロット配列の IAM (Index Allocation Map) ページに 1 ページが割り当てられたことを示す、REPAIR からの情報メッセージです。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  

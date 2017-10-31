---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d7733792d9133f5db50df313b9f99bbc30f10f2e
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|21862|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21862|  
|メッセージ テキスト|FILESTREAM 列は、同期方法 'database snapshot' または 'database snapshot character' を使用して、パブリケーションでパブリッシュすることはできません。|  
  
## <a name="explanation"></a>説明  
データベース スナップショットから FILESTREAM データにアクセスできないため、パブリケーションの同期方法に *database snapshot* パラメーターまたは *database_snapshot_character* パラメーターが指定されている場合、スナップショット エージェントは FILESTREAM データを読み取ることができません。  
  
## <a name="user-action"></a>ユーザーの操作  
パブリケーションの同期方法を *database snapshot* または *database_snapshot_character* 以外の方法に変更するか、パブリケーションから FILESTREAM 列を除外します。  
  


---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9cf2edc55900ceb2181d5ae0d300300376f3ecbe
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553487"
---
# <a name="mssqlserver_1807"></a>MSSQLSERVER_1807
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1807|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|CANNOT_EX_LOCK|  
|メッセージ テキスト|データベース '%.*ls' を排他的にロックできませんでした。 後でこの操作を再試行してください。|  
  
## <a name="explanation"></a>説明  
 データベースに対して排他的なアクセスを必要とする操作で、排他ロックを獲得できませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 このデータベースに対する接続をすべて切断するか、クエリを後で再試行します。  
  
  

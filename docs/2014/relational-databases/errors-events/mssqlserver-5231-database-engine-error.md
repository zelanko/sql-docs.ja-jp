---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6c57150dd8fac6dab1c2c9cf6fdf7cefbdb1b5f8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62913589"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5231|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|メッセージ テキスト|オブジェクト ID O_ID (オブジェクト 'NAME') : このオブジェクトを確認のためにロックしようとして、デッドロックが発生しました。 このオブジェクトはスキップされたので、処理されません。|  
  
## <a name="explanation"></a>説明  
 DBCC がオブジェクトをロックしようとしてデッドロックが発生し、DBCC がデッドロック対象として選択されました。 このオブジェクトは処理されません。  
  
## <a name="user-action"></a>ユーザーの操作  
 なし  
  
  

---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa4307f1cd72ea797ccf0a607796dca32ef4e1e6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411611"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
    
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
  
  

---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 465f47fd69f8e6477ede13892a079f069042c57b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553037"
---
# <a name="mssqlserver_8712"></a>MSSQLSERVER_8712
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8712|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|USEPLAN_ERR_NO_INDEX|  
|メッセージ テキスト|USE PLAN ヒントで指定したインデックス '%.*ls' が存在しません。 既存のインデックスを指定するか、指定した名前を持つインデックスを作成してください。|  
  
## <a name="explanation"></a>説明  
 USE PLAN ヒントで指定したインデックスが存在しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 USE PLAN ヒントで指定したすべてのインデックスが存在することを確認します。  
  
## <a name="see-also"></a>参照  
 [クエリ ヒント &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)   
 [プラン ガイド](../performance/plan-guides.md)  
  
  

---
title: MSSQLSERVER_12304 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
caps.latest.revision: "4"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 7fc3019b148e9ac0ca278b69f55d2e2c67b33ac0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver12304"></a>MSSQLSERVER_12304
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|12304|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|メッセージ テキスト|ネイティブ コンパイル ストアド プロシージャのコンテキスト外にある型を使用する場合は、自らの任意の列と共に IDENTITY プロパティを使用するメモリ最適化テーブルを使用することはサポートされていません。|  
  
## <a name="user-action"></a>ユーザーの操作  
自らの任意の列と共に IDENTITY プロパティを使用するメモリ最適化テーブル型を使用しないでください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

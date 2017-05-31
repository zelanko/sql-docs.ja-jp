---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d4523266142da60eb89136be6209a5944cecbd5a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|360|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DML_UPDATE_SPARSE_AND_COLSET|  
|メッセージ テキスト|INSERT、UPDATE、または MERGE ステートメントの対象の列リストには、スパース列と、スパース列を含む列セットの両方を含めることはできません。 スパース列と列セットの両方ではなく、いずれかを含めるようにステートメントを書き直してください。|  
  
## <a name="explanation"></a>説明  
列セットは、型指定されていない XML 表現であり、テーブルの複数の列を 1 つにまとめて構造化した出力です。 列セットと、列セットに含まれる列の両方を変更しようとして、同じ列への参照が 2 つ発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
列または列セットのいずれかへの参照を含めるようにステートメントを書き直して、両方をステートメントに含めないでください。  
  


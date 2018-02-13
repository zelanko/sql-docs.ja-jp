---
title: "SQLXML における Diffgram のガイドラインと制限 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2af871b240d318aaa027402a52a9c31498521b99
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>SQLXML における DiffGram のガイドラインと制限
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
SQLXML 4.0 で DiffGram を使用するときには、次の点に注意してください。  
  
-   バイナリ ラージ オブジェクト (BLOB) のような種類**text、ntext**イメージでは使用できません、  **\<diffgr: する前に >**これが含まれるためそれらで使用するため、Diffgram を使用する場合ブロック同時実行制御。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。 列の間で比較するため、WHERE 句で LIKE キーワードが使用するなど、**テキスト**データ型です。 ただし、比較は失敗ここで、データのサイズは 8 K を超える BLOB 型の場合。  
  
-   特殊文字を**ntext**データ BLOB 型の比較の制限により SQLXML 4.0 で問題が発生することができます。 "[Serializable]"の使用など、  **\<diffgr: する前に >**同時実行制御の列のチェックで使用する場合、DiffGram のブロック**ntext**型は、次の SQLOLEDB で失敗エラーの説明:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  

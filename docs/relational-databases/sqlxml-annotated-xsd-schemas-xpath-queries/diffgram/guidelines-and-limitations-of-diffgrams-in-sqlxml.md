---
title: SQLXML における Diffgram のガイドラインと制限 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 64f19e8d7b5e67311f21b79c6f36572d9b2240d8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073450"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>SQLXML における DiffGram のガイドラインと制限
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SQLXML 4.0 で DiffGram を使用するときには、次の点に注意してください。  
  
-   バイナリ ラージ オブジェクト (BLOB) のような種類**text、ntext**でイメージを使用する必要があります、  **\<diffgr: する前に >** で使用するために含まれてはこのため、Diffgram を使用する場合ブロック同時実行制御。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。 列の比較するには、WHERE 句で LIKE キーワードが使用されるなど、**テキスト**データを入力します。 ただし、比較は失敗、データのサイズが 8 K を超える BLOB 型の場合。  
  
-   特殊文字**ntext**データ BLOB 型の比較の制限により SQLXML 4.0 で問題が発生することができます。 "[Serializable]"の使用など、  **\<diffgr: する前に >** 同時実行制御の列のチェックで使用する場合、DiffGram のブロック**ntext**型は、次の SQLOLEDB で失敗エラーの説明:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  

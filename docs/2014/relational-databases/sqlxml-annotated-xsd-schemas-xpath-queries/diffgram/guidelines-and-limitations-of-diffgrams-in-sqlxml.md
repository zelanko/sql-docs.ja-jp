---
title: SQLXML における Diffgram のガイドラインと制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 61f1c621a44605db890c9f63ec0a7d1c71212e3c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703155"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>SQLXML における DiffGram のガイドラインと制限
  SQLXML 4.0 で DiffGram を使用するときには、次の点に注意してください。  
  
-   ph x="1" /&gt; や image のようなバイナリ ラージ オブジェクト (BLOB) 型は、DiffGram の `<diffgr:before>` ブロックでは使用しないでください。使用すると、これらがコンカレンシー制御で使用され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で、BLOB 型の比較の制限によって問題が発生する可能性があります。 たとえば、`text` データ型の列を比較するには WHERE 句で LIKE キーワードを使用しますが、データ サイズが 8 KB を超える BLOB 型の場合、この比較は失敗します。  
  
-   `ntext` データで特殊文字を使用すると、BLOB 型の比較の制限によって、SQLXML 4.0 で問題が発生する可能性があります。 たとえば、DiffGram の `<diffgr:before>` ブロックに "[Serializable]" を使用すると、`ntext` 型列に対するコンカレンシー チェックで操作が失敗し、次の SQLOLEDB エラー説明が返されます。  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  

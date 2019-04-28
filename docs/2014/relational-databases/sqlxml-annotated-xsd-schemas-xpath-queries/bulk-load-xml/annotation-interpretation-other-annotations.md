---
title: その他の注釈 (SQLXML 4.0) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 668e26430e97a1e7d34e0e420966b975874224c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62717899"
---
# <a name="other-annotations-sqlxml-40"></a>その他の注釈 (SQLXML 4.0)
  前のトピックで説明した注釈に加えて、XML 一括読み込みでは、その他の注釈が次のように解釈されます。  
  
 `sql:id-prefix`  
 スキーマで XML データのプレフィックスを指定した場合、XML 一括読み込みでは Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのデータの送信前にプレフィックスが削除されます。  
  
 `sql:use-cdata`  
 XML 一括読み込みでは、CDATA セクションに格納されているテキストが読み取られ、それが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。  
  
 `sql:url-encode`  
 XML 一括読み込みでは、この注釈はサポートされません。 たとえば、XML データ入力に URL を指定することはできません。また、XML 一括読み込みで、指定した場所からデータを読み込んでデータベースに格納することはできません。  
  
 `sql:is-mapping-schema`  
 XML 一括読み込みではこの注釈はサポートされず、`sql:id` もサポートされません。  
  
> [!NOTE]  
>  XML 一括読み込みでは、インライン マッピング スキーマはサポートされません。  
  
 `sql:key-fields`  
 XML 一括読み込みでは、この注釈は常に無視されます。  
  
## <a name="see-also"></a>参照  
 [注釈の解釈&#40;SQLXML 4.0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  

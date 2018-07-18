---
title: その他の注釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01e0af9b72790b8a2ddf396434c84f25ee270313
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223132"
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
  
  

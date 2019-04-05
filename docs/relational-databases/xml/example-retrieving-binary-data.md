---
title: '例: バイナリ データの取得 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1479883b1e311ad625e4a169d2c7e82d00125d57
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512409"
---
# <a name="example-retrieving-binary-data"></a>例:バイナリ データの取得
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  次のクエリでは、 **varbinary(max)** 型の列に格納された製品の写真が返されます。 クエリで `BINARY BASE64` オプションが指定されているので、バイナリ データは Base64 エンコード形式で返されます。  
  
## <a name="example"></a>例  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 結果を次に示します。  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  

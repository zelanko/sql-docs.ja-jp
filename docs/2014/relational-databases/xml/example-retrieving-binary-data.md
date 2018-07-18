---
title: '例 : バイナリ データの取得 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4200917619f7b36f34d39754cc548a5a3cb3458
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280768"
---
# <a name="example-retrieving-binary-data"></a>例 : バイナリ データの取得
  次のクエリでは、`varbinary(max)` 型の列に格納された製品の写真が返されます。 クエリで `BINARY BASE64` オプションが指定されているので、バイナリ データは Base64 エンコード形式で返されます。  
  
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
 [FOR XML での RAW モードの使用](use-raw-mode-with-for-xml.md)  
  
  

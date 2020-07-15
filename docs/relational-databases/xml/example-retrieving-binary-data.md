---
title: '例: バイナリ データの取得 | Microsoft Docs'
description: FOR XML 句で RAW および BINARY BASE64 オプションを使用して、バイナリ データを取得する SQL クエリの例を示します。
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: RothJa
ms.author: jroth
ms.openlocfilehash: 08010e294b1b143c941774912d661a53c021a6ab
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632788"
---
# <a name="example-retrieving-binary-data"></a>例:バイナリ データの取得

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

次のクエリでは、 **varbinary(max)** 型の列に格納された製品の写真が返されます。 クエリで `BINARY BASE64` オプションが指定されているので、バイナリ データは Base64 エンコード形式で返されます。

## <a name="example"></a>例

```sql
USE AdventureWorks2012;
GO
SELECT ProductPhotoID, ThumbNailPhoto
FROM Production.ProductPhoto
WHERE ProductPhotoID=1
FOR XML RAW, BINARY BASE64 ;
GO
```

次のような結果が予想されます。

```console
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>
```

## <a name="see-also"></a>参照

[FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

---
title: PATH モードでの名前空間のサポート | Microsoft Docs
description: PATH モードを使用して、SELECT クエリから XML を生成する場合の名前空間のサポートについて学習します。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb8691f3cdd847a626db99a43e949a4b87a5aefe
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85661644"
---
# <a name="namespace-support-in-path-mode"></a>PATH モードでの名前空間のサポート
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  PATH モードでは、WITH NAMESPACES を使用することで名前空間がサポートされます。 たとえば、次のクエリは WITH NAMESPACES 構文を使用して、後続の SELECT ステートメントで使用できる名前空間 ("a:") を宣言する例を示しています。  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>例  
 次のサンプルでは、PATH モードで SELECT クエリから XML を生成する例を示します。 これらのクエリの多くは、ProductModel テーブルの Instructions 列に格納されている、自転車製造手順の XML ドキュメントに対して指定されています。  
  
## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  

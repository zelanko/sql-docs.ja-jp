---
title: PATH モードでの名前空間のサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8e4a5e775da2811948879e4a67ace7a11a9ed807
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178391"
---
# <a name="namespace-support-in-path-mode"></a>PATH モードでの名前空間のサポート
  PATH モードでは、WITH NAMESPACES を使用することで名前空間がサポートされます。 たとえば、次のクエリは WITH NAMESPACES 構文を使用して、後続の SELECT ステートメントで使用できる名前空間 ("a:") を宣言する例を示しています。  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>使用例  
 次のサンプルでは、PATH モードで SELECT クエリから XML を生成する例を示します。 これらのクエリの多くは、ProductModel テーブルの Instructions 列に格納されている、自転車製造手順の XML ドキュメントに対して指定されています。  
  
## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md)  
  
  
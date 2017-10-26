---
title: "テーブル名 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 480ca31108b608139b5563f0c18d1fa020e76f75
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="table-names"></a>テーブル名
ときに、dBASE、Excel、Paradox、またはドライバーが使用されるテキスト、テーブル名に発生する SELECT や DELETE の FROM 句で、INSERT INTO 句の後に、更新後に CREATE TABLE、および DROP TABLE には、有効なパスを含めることができます、プライマリ名およびファイルという名前の拡張機能.  
  
 SQL ステートメントの他の場所のテーブル名の使用方法は、パスまたは拡張機能の使用をサポートしていませんが、プライマリの名前 (たとえば、EMP から C:\ABC\EMP) のみを受け入れます。  
  
 相関名 (エイリアス) を使用できます。 例:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```


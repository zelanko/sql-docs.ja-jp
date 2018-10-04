---
title: テーブル名 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d72d7868d0e19719ea7992bdb8ccd1f61f3718d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755736"
---
# <a name="table-names"></a>テーブル名
ときに、dBASE、Excel、Paradox、またはドライバーが使用されるテキスト、テーブル名で発生するは、SELECT や DELETE FROM 句と更新の後、insert INTO 句の後に CREATE TABLE、および DROP TABLE には、有効なパスを含めることができます、プライマリ名およびファイルの名前の拡張機能.  
  
 SQL ステートメントの他の場所でテーブル名の使用は、パスまたは拡張機能の使用をサポートしていませんがプライマリの名前 (たとえば、EMP から C:\ABC\EMP) のみを受け入れます。  
  
 相関名 (別名) を使用できます。 以下に例を示します。  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```

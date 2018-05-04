---
title: テーブル名 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1b1032ccda48d5a645e9992e2c501c851f51b7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="table-names"></a>テーブル名
ときに、dBASE、Excel、Paradox、またはドライバーが使用されるテキスト、テーブル名に発生する SELECT や DELETE の FROM 句で、INSERT INTO 句の後に、更新後に CREATE TABLE、および DROP TABLE には、有効なパスを含めることができます、プライマリ名およびファイルという名前の拡張機能.  
  
 SQL ステートメントの他の場所のテーブル名の使用方法は、パスまたは拡張機能の使用をサポートしていませんが、プライマリの名前 (たとえば、EMP から C:\ABC\EMP) のみを受け入れます。  
  
 相関名 (エイリアス) を使用できます。 以下に例を示します。  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```

---
title: SET NULL Command |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f8addb9b4c7c200ee8f213bdd959067039ccfff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063671"
---
# <a name="set-null-command"></a>SET NULL コマンド
ALTER TABLE-SQL、CREATE TABLE SQL、および INSERT-SQL コマンドで null 値をどのようにサポートするかを決定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値は、Visual FoxPro の既定値は OFF です)。ALTER TABLE および CREATE TABLE で作成されたテーブル内のすべての列で null 値を許容することを指定します。 列の定義に NOT NULL 句を含めることにより、テーブル内の列の null 値のサポートを無効にできます。  
  
 また、insert-sql が、INSERT-SQL VALUE 句に含まれていない列に null 値を挿入することを指定します。 INSERT-SQL では、null 値を許容する列にのみ null 値が挿入されます。  
  
 OFF  
 ALTER TABLE および CREATE TABLE で作成されたテーブル内のすべての列で null 値を許容しないように指定します。 列の定義に NULL 句を含めることによって、ALTER TABLE と CREATE TABLE の列に null 値のサポートを指定できます。  
  
 また、insert-SQL が、INSERT-SQL VALUE 句に含まれていない列に空白の値を挿入することを指定します。  
  
## <a name="remarks"></a>解説  
 SET NULL は、ALTER TABLE、CREATE TABLE、および INSERT によって null 値がサポートされる方法にのみ影響します。 他のコマンドは、SET NULL によって影響を受けません。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE-SQL コマンド](../../odbc/microsoft/alter-table-sql-command.md)   
 [CREATE TABLE-SQL コマンド](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL コマンド](../../odbc/microsoft/insert-sql-command.md)

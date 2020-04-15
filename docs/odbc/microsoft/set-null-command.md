---
title: NULL コマンドを設定する |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c83c9ef9f8a0ce143308b73d8df09b05fb2cdea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300812"
---
# <a name="set-null-command"></a>SET NULL コマンド
ALTER TABLE コマンド、テーブルの作成 - SQL コマンド、および INSERT - SQL コマンドの場合に、NULL 値がどのようにサポートされるかを決定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値、ビジュアル FoxPro の既定値はオフです)。ALTER TABLE および CREATE TABLE で作成された表のすべての列が NULL 値を許可することを指定します。 列の定義に NOT NULL 句を含めることで、テーブル内の列に対する NULL 値のサポートをオーバーライドできます。  
  
 また、INSERT - SQL は、INSERT - SQL VALUE 句に含まれていない列に NULL 値を挿入することを指定します。 INSERT - SQL は NULL 値を許容する列にのみ NULL 値を挿入します。  
  
 OFF  
 ALTER TABLE および CREATE TABLE で作成された表のすべての列が NULL 値を許可しないことを指定します。 列の定義に NULL 句を含めることで、ALTER TABLE および CREATE TABLE の列に対して NULL 値のサポートを指定できます。  
  
 また、INSERT - SQL は、INSERT - SQL VALUE 句に含まれていない列に空白値を挿入することを指定します。  
  
## <a name="remarks"></a>解説  
 SET NULL は、表の変更、表の作成、および挿入 - SQL でのヌル値のサポート方法にのみ影響します。 その他のコマンドは、SET NULL の影響を受けません。  
  
## <a name="see-also"></a>参照  
 [テーブルの変更 - SQL コマンド](../../odbc/microsoft/alter-table-sql-command.md)   
 [テーブルの作成 - SQL コマンド](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL コマンド](../../odbc/microsoft/insert-sql-command.md)

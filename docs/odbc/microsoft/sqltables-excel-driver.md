---
title: SQLTables (Excel Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89157178aa9c134bdb1b9518343007adb1e1e05f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132423"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*szTableOwner*|すべてのドライバーで所有者名がサポートされていないため、 *Sztableowner*の有効な引数は NULL だけです。 *Sztableowner*を NULL に設定すると、すべてのテーブルが返されます。 TABLE_OWNER 列に NULL が返されます。|  
|*szTableQualifier*|Microsoft Excel 3.0 または4.0 ドライバーが使用されている場合、既存のテーブルの名前ではない*Sztablequalifier*の値を使用して**sqltables**を呼び出すと、ドライバーによってその名前のテーブルが作成されます。<br /><br /> TABLE_QUALIFIER 列では、 **Sqltables**はディレクトリへのパスを返します。|  
|*SzTableType*|Microsoft Excel 3.0 または4.0 の場合、サポートされているテーブル型は "TABLE" だけです。<br /><br /> Microsoft Excel ファイルの新しいバージョンでは、シート名 (末尾に "$" があるテーブル) に対して "システムテーブル" が返され、ワークシート内のテーブルに対して "TABLE" が返されます。|

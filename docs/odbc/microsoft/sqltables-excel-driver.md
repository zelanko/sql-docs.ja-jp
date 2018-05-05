---
title: SQLTables (Excel ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2921d9e047e03cae092e5c0e7d2fcd4e4f8f24c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバーに固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|引数|コメント|  
|--------------|--------------|  
|*szTableOwner*|唯一の有効な引数*szTableOwner* NULL では、ドライバーのサポート所有者名。 *SzTableOwner*を NULL に設定すると、すべてのテーブルが返されます。 TABLE_OWNER 列に NULL が返されます。|  
|*szTableQualifier*|Microsoft Excel 3.0 または 4.0 のドライバーを使用する場合、呼び出す場合は、 **SQLTables**に値を持つ*szTableQualifier*外にある既存のテーブルの名前、ドライバーはその名前を持つテーブルを作成します。<br /><br /> TABLE_QUALIFIER 列で**SQLTables**ディレクトリへのパスを取得します。|  
|*SzTableType*|Microsoft Excel 3.0 または 4.0 では、"TABLE"はサポートされている唯一のテーブル型です。<br /><br /> 以降のバージョンの Microsoft Excel ファイルでは、シートの名前 (末尾に「$」でテーブル) の「システム テーブル」が返されます、ワークシート内のテーブルの"TABLE"が返されます。|

---
title: SQL テーブル (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5467fc8c1717d5ceb548b3950a0894fd2a1b4499
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299287"
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 **SQLTables**ステートメントのパラメーターで指定されたテーブル名の一覧を返します。 パラメーターを指定しない場合は、現在のデータ ソースに格納されているテーブル名を返します。 ドライバーは、結果セットとして情報を返します。  
  
 列挙型の呼び出しは、リモート ビューまたはローカル のパラメーター化されたビューの結果セット エントリを受け取りません。 ただし、一意のテーブル名指定子を持つ**SQLTables の**呼び出しは、その名前を持つビューが存在する場合、このようなビューに一致するものを見つけます。これにより、新しいテーブルを作成する前に、API を使用して名前の競合をチェックできます。  
  
> [!NOTE]  
>  Visual FoxPro ODBC ドライバは、両方のタイプのテーブルがシステム上の同じディレクトリに格納されている場合でも、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)テーブルと[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)を区別します。 データ ソースが空きテーブルのディレクトリである場合、Visual FoxPro ODBC ドライバーは、データベースに関連付けられているテーブルのカタログまたは名前を返しません。  
  
 詳細については *、『ODBC プログラマ リファレンス*』の[「SQLTables」](../../odbc/reference/syntax/sqltables-function.md)を参照してください。

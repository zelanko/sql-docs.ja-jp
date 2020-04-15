---
title: SQLTables (テキスト ファイル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 938ceba5da25d176628d5c1d9875383d977e3aec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299332"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|引数|説明|  
|--------------|--------------|  
|*所有者*|*szTableOwner*の唯一の有効な引数は、どのドライバーも所有者名をサポートしていないため NULL です。 *szTableOwner が*NULL に設定されている場合、すべてのテーブルが返されます。 TABLE_OWNER列に NULL が返されます。|  
|*修飾子*|TABLE_QUALIFIER列では **、SQLTables は**ディレクトリへのパスを返します。|  
|*SZ テーブルタイプ*|"TABLE" はサポートされている唯一のテーブルタイプです。<br /><br /> テキスト ドライバーを使用すると **、SQLTables**によって返されるファイルの一覧は **、ODBC テキスト セットアップ**ダイアログ ボックスの **[拡張子リスト**] ボックスのファイル拡張子によって決まります。|

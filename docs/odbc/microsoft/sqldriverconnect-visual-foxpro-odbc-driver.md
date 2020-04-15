---
title: コネクト ( ビジュアル フォックスプロ ODBC ドライバー ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307093"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 既存のデータ ソース ([データベース](../../odbc/microsoft/visual-foxpro-terminology.md)または[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリ) に接続します。 ODBC 属性キーワード UID および PWD は無視されます。 次の表に、サポートされているその他の属性キーワードを示します。  
  
|ODBC 属性キーワード|属性値|  
|----------------------------|---------------------|  
|DSN (DSN)||  
|UID|Visual FoxPro ODBC ドライバーによって無視されますが、エラーは生成されません。|  
|PWD|Visual FoxPro ODBC ドライバーによって無視されますが、エラーは生成されません。|  
|Driver|名前と名前と場所、ビジュアル フォックスプロ ODBC ドライバー。ドライバー マネージャーによって実装されます。|  
  
|ビジュアル フォックスプロ ODBC ドライバー属性キーワード|属性値|  
|-------------------------------------------------|---------------------|  
|バックグラウンドフェッチ|「はい」または「いいえ」|  
|[部単位で印刷]|「機械」またはその他の照合シーケンス。 サポートされる照合シーケンスのリストについては[、SET COLLATE](../../odbc/microsoft/set-collate-command.md)を参照してください。|  
|説明||  
|排他的|「はい」または「いいえ」|  
|SourceDB|空[き](../../odbc/microsoft/visual-foxpro-terminology.md)テーブルが 0 個以上あるディレクトリへの完全修飾パス、[またはデータベース](../../odbc/microsoft/visual-foxpro-terminology.md)の絶対パスとファイル名。|  
|SourceType|"DBC" または "DBF"|  
|Version||  
  
 データ ソース名が指定されていない場合、ドライバー マネージャーは *、(fDriverCompletion*引数の設定に応じて) 情報をユーザーに求め、続行します。 詳細な情報が必要な場合は、プロンプト ダイアログが表示されます。  
  
 詳細については *、ODBC プログラマ リファレンス*の[「SQLDriverConnect」](../../odbc/reference/syntax/sqldriverconnect-function.md)を参照してください。

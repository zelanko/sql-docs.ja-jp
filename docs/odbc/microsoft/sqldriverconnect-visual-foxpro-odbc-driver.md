---
title: SQLDriverConnect (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6fd8f3be1213a91195cd74a8b723629e2c5833f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053894"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル1  
  
 既存のデータソースに接続します。これは、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)または[フリーテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリのいずれかになります。 ODBC 属性キーワード UID と PWD は無視されます。 次の表に、サポートされているその他の属性キーワードを示します。  
  
|ODBC 属性キーワード|属性名|  
|----------------------------|---------------------|  
|DSN (DSN)||  
|UID|Visual FoxPro ODBC ドライバーでは無視されますが、エラーは発生しません。|  
|PWD|Visual FoxPro ODBC ドライバーでは無視されますが、エラーは発生しません。|  
|Driver|Visual FoxPro ODBC ドライバーの名前と場所です。ドライバーマネージャーによって実装されます。|  
  
|Visual FoxPro ODBC ドライバーの属性キーワード|属性名|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Yes" または "No"|  
|[部単位で印刷]|"コンピューター" またはその他の照合シーケンス。 サポートされている照合シーケンスの一覧については、「 [COLLATE の設定](../../odbc/microsoft/set-collate-command.md)」を参照してください。|  
|[説明]||  
|排他的|"Yes" または "No"|  
|SourceDB|0個以上の[フリーテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)を含むディレクトリへの完全修飾パス、または[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)の絶対パスとファイル名。|  
|SourceType|"DBC" または "DBF"|  
|Version||  
  
 データソース名が指定されていない場合、ドライバーマネージャーは、 *Fdrivercompletion*引数の設定に応じて、ユーザーに情報の入力を求め、続行します。 詳細情報が必要な場合は、Visual FoxPro ODBC ドライバーによって [プロンプト] ダイアログが表示されます。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) 」を参照してください。

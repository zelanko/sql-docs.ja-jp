---
title: SQLDriverConnect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d1aedce0d1e2888a4aada3a92cf0eb5973d489a5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904147"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 いずれかになりますが、既存のデータ ソースに接続する、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)またはディレクトリの[テーブルの空き](../../odbc/microsoft/visual-foxpro-terminology.md)です。 UID および PWD ODBC 属性キーワードは無視されます。 次の表には、追加のサポートされている属性のキーワードが一覧表示します。  
  
|ODBC 属性キーワード|属性値|  
|----------------------------|---------------------|  
|DSN (DSN)||  
|UID|Visual FoxPro ODBC ドライバーでは無視されますが、エラーを生成しません。|  
|PWD|Visual FoxPro ODBC ドライバーでは無視されますが、エラーを生成しません。|  
|Driver|Visual FoxPro ODBC ドライバーの場所と名前ドライバー マネージャーによって実装されます。|  
  
|Visual FoxPro ODBC ドライバー属性のキーワード|属性値|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Yes"または"No"|  
|[部単位で印刷]|「マシン」、またはその他の照合順序。 サポートされている照合順序の一覧は、次を参照してください。 [COLLATE 設定](../../odbc/microsoft/set-collate-command.md)です。|  
|Description||  
|[Exclusive]|"Yes"または"No"|  
|SourceDB|0 個以上完全修飾パスを含むディレクトリを[テーブルの空き](../../odbc/microsoft/visual-foxpro-terminology.md)、またはの絶対パスとファイル名、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)です。|  
|[SourceType]|"DBC"または"DBF"|  
|バージョン||  
  
 データ ソース名が指定されていない場合、ドライバー マネージャーを求める情報 (の設定に応じて、 *fDriverCompletion*引数) して続行します。 詳細については、必要なは、Visual FoxPro ODBC ドライバーのプロンプト ダイアログが表示されます。  
  
 詳細については、次を参照してください。 [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)で、 *ODBC プログラマ リファレンス*です。

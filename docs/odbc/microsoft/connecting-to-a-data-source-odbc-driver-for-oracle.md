---
title: データ ソースへの接続 (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ef567c9e3c7b63e7f5044de699750de856f3e52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281302"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>データ ソース (ODBC Driver for Oracle) への接続
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ODBC アプリケーションは、接続情報をさまざまな方法で渡すことができます。 たとえば、アプリケーションでは、ドライバーは常に接続情報のユーザーを求める場合があります。 または、アプリケーションは、データ ソース接続を指定する接続文字列を期待する場合があります。 データ ソースへの接続方法は、ODBC アプリケーションで使用する接続方法によって異なります。  
  
 データ ソースに接続する一般的な方法の 1 つは、[データ ソース] ダイアログ ボックスを使用することです。 ODBC アプリケーションがダイアログ ボックスを使用するように設定されている場合、ダイアログ ボックスが表示され、適切なデータ ソース接続情報の入力を求めるプロンプトが表示されます。  
  
 接続文字列 を使用してデータ[ソースに接続](../../odbc/microsoft/connection-string-format-and-attributes.md)することもできます。  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>ダイアログ ボックスを使用してデータ ソースに接続するには  
  
1.  [データ ソース] ダイアログ ボックスが表示されたら、Oracle データ ソースを選択し、[OK] をクリックします。 ［接続］ダイアログ ボックスが表示されます。  
  
2.  [接続] ダイアログ ボックスの適切な情報を入力し、[OK] をクリックします。  
  
 接続情報が検証されると、アプリケーションは ORACLE 用 ODBC ドライバーを使用して、データ ソースに含まれる情報にアクセスできます。

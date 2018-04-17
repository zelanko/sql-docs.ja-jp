---
title: 接続文字列の形式と属性 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7a16ee8409a96433929e2b900e3f68c41573a8b1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connection-string-format-and-attributes"></a>接続文字列の形式と属性
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 一部のアプリケーションは、ダイアログ ボックスを使用する代わりに、データ ソース接続情報を指定する接続文字列を必要があります。 接続文字列は、ドライバーがデータ ソースに接続する方法を指定する属性の数で構成されます。 属性は、特定のドライバーが適切なデータ ソース接続を行うにを知る必要がある情報を識別します。 属性のさまざまなセットがあり、それぞれのドライバーが、接続文字列の形式が同じでは常にします。 接続文字列には、次の形式があります。  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Microsoft ODBC Driver for Oracle を使用すると、ドライバーの最初のバージョンの接続文字列の形式をサポートしている`CONNECTSTRING`の代わりに =`SERVER=`です。  
  
 Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する`Trusted_Connection=yes`接続文字列でユーザー ID とパスワード情報の代わりにします。  
  
 データ ソースを指定する必要があります、UID、PWD、サーバー (または CONNECTSTRING) を指定しない場合の名前とドライバーの属性です。 ただし、その他のすべての属性は省略できます。 関連する DSN タブで指定されている場合は、属性を指定しないと、その属性の既定値、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックス。 属性の値は、大文字小文字を区別可能性があります。  
  
 接続文字列の属性は次のとおりです。  
  
|属性|Description|既定値|  
|---------------|-----------------|-------------------|  
|DSN (DSN)|ドライバー タブで、データ ソース名が一覧表示、 **ODBC データ ソース アドミニストレーター**  ダイアログ ボックス。|""|  
|PWD|アクセスする Oracle サーバーのパスワード。 このドライバーは、Oracle によってパスワードで配置の制限をサポートします。|""|  
|SERVER|アクセスする Oracle サーバーへの接続文字列。|""|  
|UID|Oracle サーバーのユーザー名。 システムに応じて、この属性できない可能性があります省略可能なつまり、特定のデータベースとテーブルが必要ですがこの属性セキュリティ上の理由。<br /><br /> 「/」を使用して Oracle の使用のシステムの認証を操作します。|""|  
|BUFFERSIZE|列をフェッチするときに使用する最適なバッファー サイズ。<br /><br /> ドライバーは、Oracle サーバーから 1 つのフェッチには、このサイズのバッファーを入力するための十分な行が返されます。 ようにフェッチを最適化します。 大きな値は、大量のデータをフェッチする場合は、パフォーマンスを向上する傾向があります。|65535|  
|SYNONYMCOLUMNS|この値が true (1) SQLColumn () API 呼び出しは、列情報を返します。 それ以外の場合、SQLColumn に関するページ () は、テーブルやビューの列のみを返します。 ODBC Driver for Oracle は、この値が設定されていないときに、高速アクセスを提供します。|1|  
|REMARKS|この値が true (1)、ドライバーは、「解説」列を返します、 [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)結果セットです。 ODBC Driver for Oracle は、この値が設定されていないときに、高速アクセスを提供します。|0|  
|StdDayOfWeek|ODBC 標準の DAYOFWEEK スカラーを強制します。 既定ではこれが有効ですが、ローカライズ版を必要とするユーザーは、Oracle の値をそのまま使用する動作を変更できます。|1|  
|GuessTheColDef|ドライバーのゼロ以外の値を返すかどうかを指定、 *cbColDef*の引数**SQLDescribeCol**です。 ここではありません Oracle 定義のスケールでは、計算など、数値列にのみ適用される列とせず、有効桁数または小数点数として定義されている列。 A **SQLDescribeCol** Oracle でその情報が提供されない場合に、有効桁数の返します 130 を呼び出します。|0|  
  
 たとえば、MyOracleServerOracle サーバーと Oracle ユーザー MyUserID MyDataSource データ ソースに接続する接続文字列は次のようになります。  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 オペレーティング システムの認証と MyOtherOracleServerOracle サーバーを使用して MyOtherDataSource データ ソースに接続する接続文字列は次のようになります。  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```

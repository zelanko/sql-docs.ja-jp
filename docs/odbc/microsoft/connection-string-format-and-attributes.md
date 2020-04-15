---
title: 接続文字列の形式と属性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connection strings
ms.assetid: 0c360112-8720-4e54-a1a6-b9b18d943557
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d95866976d2e83c058f83b3a0ae5e9a4e8888ed1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281152"
---
# <a name="connection-string-format-and-attributes"></a>接続文字列の形式と属性
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ダイアログ ボックスを使用する代わりに、一部のアプリケーションでは、データ ソース接続情報を指定する接続文字列が必要になる場合があります。 接続文字列は、ドライバーがデータ ソースに接続する方法を指定する属性の数で構成されます。 属性は、ドライバーが適切なデータ ソース接続を行う前に知る必要がある特定の情報を識別します。 各ドライバーは、異なる属性のセットを持つことができますが、接続文字列の形式は常に同じです。 接続文字列の形式は次のとおりです。  
  
```  
"DSN=data-source-name[;SERVER=value] [;PWD=value] [;UID=value] [;<Attribute>=<value>]"  
```  
  
> [!NOTE]  
>  Oracle 用の ODBC ドライバーは、ドライバーの最初のバージョンの接続文字列形式をサポート`CONNECTSTRING``SERVER=`しています。  
  
 Windows 認証をサポートするデータ ソース プロバイダに接続する場合は、接続文字列`Trusted_Connection=yes`でユーザー ID とパスワード情報の代わりに指定する必要があります。  
  
 UID、PWD、サーバー (または接続ストリング) およびドライバー属性を指定しない場合は、データ・ソース名を指定する必要があります。 ただし、その他の属性はすべて省略可能です。 属性を指定しない場合、その属性は既定で **[ODBC データ ソース アドミニストレータ**]ダイアログ ボックスの [DSN] タブで指定された属性になります。 属性値は大文字と小文字を区別する場合があります。  
  
 接続文字列の属性は次のとおりです。  
  
|属性|説明|既定値|  
|---------------|-----------------|-------------------|  
|DSN (DSN)|[ODBC データ ソース**アドミニストレータ**] ダイアログ ボックスの [ドライバ] タブに表示されるデータ ソース名。|""|  
|PWD|アクセスする Oracle サーバーのパスワード。 このドライバは、Oracle がパスワードに適用する制限をサポートします。|""|  
|SERVER|アクセスする Oracle サーバーの接続文字列。|""|  
|UID|Oracle サーバーのユーザー名。 システムによっては、この属性はオプションではない場合があります。<br /><br /> Oracle のオペレーティング システム認証を使用するには、"/" を使用します。|""|  
|Buffersize|列をフェッチするときに使用される最適なバッファー サイズ。<br /><br /> ドライバーは、Oracle サーバーからの 1 つのフェッチがこのサイズのバッファーを埋めるために十分な行を返すできるようにフェッチを最適化します。 値が大きいほど、大量のデータをフェッチするとパフォーマンスが向上する傾向があります。|65,535|  
|シノニム列|この値が true (1) の場合、SQLColumn( ) API 呼び出しは列情報を戻します。 それ以外の場合は、SQLColumn( ) はテーブルとビューの列だけを返します。 Oracle 用 ODBC ドライバーは、この値が設定されていない場合に高速アクセスを提供します。|1|  
|REMARKS|この値が true (1) の場合、ドライバーは[SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)の結果セットの注釈列を返します。 Oracle 用 ODBC ドライバーは、この値が設定されていない場合に高速アクセスを提供します。|0|  
|ウィーク|デイフウィーク スカラーの ODBC 標準を適用します。 既定では、この機能はオンになっていますが、ローカライズ版を必要とするユーザーは、Oracle から返される動作を変更できます。|1|  
|ゲス・ザ・コルデフ|ドライバーが**SQLDescribeCol**の*引数に*0 以外の値を返すかどうかを指定します。 計算数値列や NUMBER として定義された列など、精度やスケールを指定せずに、Oracle が定義したスケールがない列にのみ適用されます。 Oracle がその情報を提供しない場合 **、SQLDescribeCol**呼び出しは精度として 130 を返します。|0|  
  
 たとえば、MyOracle サーバーOracle サーバーと Oracle ユーザーの MyUserID を使用して MyDataSource データ ソースに接続する接続文字列は次のようになります。  
  
```  
"DSN={MyDataSource};UID={MyUserID};PWD={MyPassword};SERVER={MyOracleServer}"  
```  
  
 オペレーティング システム認証と MyOtherOracleOracle サーバーを使用して MyOtherDataSource データ ソースに接続する接続文字列は、次のようになります。  
  
```  
"DSN=MyOtherDataSource;UID=/;PWD=;SERVER=MyOtherOracleServer"  
```

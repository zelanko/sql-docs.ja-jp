---
title: セットアップを使用したデータ ソースの追加と変更 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], adding
- editing data sources [ODBC], ODBC driver for Oracle
- adding data sources [ODBC], ODBC driver for Oracle
- data sources [ODBC], changing
- data sources [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], adding data sources
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae76abc902e4687e5d9891871d7d5d60598b3abc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281412"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>セットアップを使用してデータ ソースを追加および変更する
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 データ ソースは、ネットワーク ライブラリ、サーバー、データベース、およびその他の属性を含むことができるデータへのパスを識別します。 データ ソースに接続するには、ドライバー マネージャーは、特定の接続情報の Windows レジストリを確認します。  
  
 ODBC データ ソース アドミニストレータによって作成されたレジストリ エントリは、ODBC ドライバー マネージャーと ODBC ドライバーによって使用されます。 このエントリには、各データ ソースと関連付けられているドライバーに関する情報が含まれています。 データ ソースに接続するには、その接続情報をレジストリに追加する必要があります。  
  
 データ ソースを追加および構成するには[、ODBC データ ソース アドミニストレータ](../../odbc/admin/odbc-data-source-administrator.md)を使用します。 ODBC アドミニストレータは、データ ソースの接続情報を更新します。 データ ソースを追加すると、ODBC アドミニストレータによってレジストリ情報が更新されます。  
  
### <a name="to-add-a-data-source-for-windows"></a>Windows 用のデータ ソースを追加するには  
  
1.  ODBC データ ソース アドミニストレータを開きます。  
  
2.  [ODBC データ ソース アドミニストレータ] ダイアログ ボックスで、[追加] をクリックします。 [新しいデータ ソースの作成] ダイアログ ボックスが表示されます。  
  
3.  Oracle 用の ODBC を選択し、[完了] をクリックします。 [Oracle セットアップ用 ODBC] ダイアログ ボックスが表示されます。  
  
4.  [データ ソース名] ボックスに、アクセスするデータ ソースの名前を入力します。 任意の名前を選択できます。  
  
5.  [説明] ボックスに、ドライバの説明を入力します。 このオプション フィールドは、データ ソースが接続するデータベース ドライバを示します。 任意の名前を選択できます。  
  
6.  [ユーザー名] ボックスに、データベース ユーザー名 (データベース ユーザー ID) を入力します。  
  
7.  [サーバー] ボックスに、アクセスする Oracle サーバー エンジンのデータベース エイリアスまたは接続文字列を入力します。  
  
8.  [OK] をクリックして、このデータ ソースを追加します。  
  
> [!NOTE]  
>  [データ ソース] ダイアログ ボックスが表示され、ODBC アドミニストレータによってレジストリ情報が更新されます。 入力したユーザー名と接続文字列は、接続時にこのデータ ソースの既定の接続値になります。  
  
1.  [オプション] をクリックして、Oracle セットアップ用の ODBC ドライバに関する詳細な仕様を作成します。  
  
    -   **翻訳**- ロードされたデータトランスレータを選択するには、[選択]をクリックします。 デフォルトは[\<翻訳者なし>なし] です。  
  
    -   **パフォーマンス**- [カタログ関数に REMARKS を含める] チェック ボックスは、ドライバーが[SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)の結果セットの注釈列を返すかどうかを指定します。 Oracle 用 ODBC ドライバーは、この値が設定されていない場合に高速アクセスを提供します。  
  
         [SQL 列に類義語を含める] チェック ボックスは、ドライバーが列情報を返すかどうかを指定します。 **バッファサイズ**は、フェッチされたデータを受け取るために割り当てられるサイズをバイト単位で指定します。 ドライバーは、Oracle Server からの 1 つのフェッチが指定されたサイズのバッファーを埋めるために十分な行を返すできるように、フェッチを最適化します。 値が大きいほど、大量のデータをフェッチする場合にパフォーマンスが向上する傾向があります。  
  
    -   **カスタマイズ**- [ODBC DayOfWeek 標準を適用] チェック ボックスは、結果セットが ODBC で指定された曜日形式 (日曜日 = 1;土曜日 = 7)。 このチェック ボックスをオフにすると、ロケール固有の Oracle 値が返されます。  
  
         SQLDescribeCol 常**に精度の値を返す**チェック ボックスを使用して、ドライバーが**SQLDescribeCol**の*cbColDef*引数に 0 以外の値を返すかどうかを指定します。 この接続文字列属性は、精度やスケールのない NUMBER として定義された数値列や計算された数値列など、Oracle で定義されたスケールがない列にのみ適用されます。 Oracle がその情報を提供しない場合 **、SQLDescribeCol**呼び出しは精度として 130 を返します。 このチェック ボックスをオフにすると、ドライバーは代わりに列のこれらの種類の 0 を返します。  
  
2.  [追加] をクリックして別のデータ ソースを追加するか、[閉じる] をクリックして終了します。  
  
### <a name="to-modify-a-data-source-for-windows"></a>Windows のデータ ソースを変更するには  
  
1.  ODBC データ ソース アドミニストレータを開きます。 適切な DSN タブをクリックします。  
  
2.  変更する Oracle データ・ソースを選択し、「構成」をクリックします。 [Oracle セットアップ用 ODBC] ダイアログ ボックスが表示されます。  
  
3.  該当するデータ ソース フィールドを変更し、[OK] をクリックします。  
  
 このダイアログ ボックスの情報の変更が完了すると、ODBC アドミニストレータによってレジストリ情報が更新されます。

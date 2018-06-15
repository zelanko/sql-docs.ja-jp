---
title: 追加および変更データ ソースのセットアップを使用して |Microsoft ドキュメント
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
- data sources [ODBC], adding
- editing data sources [ODBC], ODBC driver for Oracle
- adding data sources [ODBC], ODBC driver for Oracle
- data sources [ODBC], changing
- data sources [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], adding data sources
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87a099890327cd4a01d5cd36cd15fc5adcaca4b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901437"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>追加して、セットアップを使用してデータ ソースを変更します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 データ ソースを識別するネットワーク ライブラリ、サーバー、データベース、およびその他の属性を含めることができるデータへのパス: ここでは、データ ソースは、Oracle データベースへのパス。 データ ソースに接続するには、ドライバー マネージャーは、特定の接続情報を Windows レジストリをチェックします。  
  
 ODBC データ ソース アドミニストレーターによって作成されたレジストリ エントリは、ODBC ドライバー マネージャーと ODBC ドライバーによって使用されます。 このエントリには、各データ ソースとその関連するドライバーに関する情報が含まれています。 データ ソースに接続することができます、前に、接続情報をレジストリに追加する必要があります。  
  
 追加し、データ ソースの構成、使用、 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)です。 Odbc データ ソース アドミニストレーターは、データ ソースの接続情報を更新します。 データ ソースを追加すると、ODBC アドミニストレーターは、レジストリ情報を更新します。  
  
### <a name="to-add-a-data-source-for-windows"></a>Windows 用のデータ ソースを追加するには  
  
1.  ODBC データ ソース アドミニストレーターを開きます。  
  
2.  ODBC データ ソース アドミニストレーター ダイアログ ボックスで、追加 をクリックします。 データ ソースの新規作成 ダイアログ ボックスが表示されます。  
  
3.  Oracle 用 Microsoft ODBC を選択し、[完了] をクリックします。 Microsoft ODBC for Oracle のセットアップ ダイアログ ボックスが表示されます。  
  
4.  [データ ソース名] ボックスにアクセスするデータ ソースの名前を入力します。 選択した任意の名前があります。  
  
5.  [説明] ボックスで、ドライバーの説明を入力します。 この省略可能なフィールドには、データ ソースに接続するデータベースのドライバーがについて説明します。 選択した任意の名前があります。  
  
6.  [ユーザー名] ボックスには、データベース ユーザー名 (データベース ユーザー ID) を入力します。  
  
7.  [サーバー] ボックスで、データベースのエイリアスを入力または接続文字列にアクセスする Oracle サーバー エンジンのします。  
  
8.  このデータ ソースを追加するには、[ok] をクリックします。  
  
> [!NOTE]  
>  データ ソース ダイアログ ボックスが表示されたら、odbc データ ソース アドミニストレーターは、レジストリ情報を更新します。 ユーザーの名前や接続文字列の入力したに接続するときにこのデータ ソースの既定の接続値になります。  
  
1.  ODBC Driver for Oracle のセットアップに関する多くの仕様を作成のオプションをクリックします。  
  
    -   **翻訳**-選択し、読み込まれたデータの変換プログラムを選択する をクリックします。 既定値は\<いいえトランスレーター >。  
  
    -   **パフォーマンス**— カタログ関数のチェック ボックスが含まれての「解説ドライバーがの「解説」列を返すどうかを指定します、 [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)結果セットです。 ODBC Driver for Oracle は、この値が設定されていないときに、高速アクセスを提供します。  
  
         SQL の列のチェック ボックスで、シノニムは、ドライバーが列の情報を返すかどうかを指定します。 **バッファー サイズ**フェッチされたデータを受信する割り当てられたバイトのサイズを指定します。 ドライバーは、Oracle サーバーから 1 つのフェッチには、指定したサイズのバッファーをいっぱいに十分な行が返されます。 ようにフェッチを最適化します。 大きな値は、大量のデータをフェッチするときにパフォーマンスを向上する傾向があります。  
  
    -   **カスタマイズ**— 強制 ODBC DayOfWeek 標準のチェック ボックスを指定するかどうか、結果セットは形式に準拠して、ODBC 指定した曜日単位 (日曜 = 1 になります。土曜 = 7)。 このチェック ボックスをオフにすると、Oracle のロケール固有の値が返されます。  
  
         SQLDescribeCol**常に有効桁数の値を返します** チェック ボックスは、ドライバーでのゼロ以外の値を返す必要があるかどうかを指定します、 *cbColDef*の引数**SQLDescribeCol**. ここではありません Oracle 定義のスケールでは、計算など、数値列にのみこの接続文字列の属性が適用される列とせず、有効桁数または小数点数として定義されている列。 A **SQLDescribeCol** Oracle でその情報が提供されない場合に、有効桁数の返します 130 を呼び出します。 このチェック ボックスをオフにした場合、ドライバーは 0 を返しますこれらの型の列の代わりにします。  
  
2.  別のデータ ソースに追加の追加 をクリックしてまたは終了を閉じる をクリックします。  
  
### <a name="to-modify-a-data-source-for-windows"></a>Windows のデータ ソースを変更するには  
  
1.  ODBC データ ソース アドミニストレーターを開きます。 適切な DSN タブをクリックします。  
  
2.  変更し、[構成] をクリックする Oracle データ ソースを選択します。 Microsoft ODBC for Oracle のセットアップ ダイアログ ボックスが表示されます。  
  
3.  適用可能なデータ ソース フィールドを変更し、[ok] をクリックします。  
  
 このダイアログ ボックスで情報の変更が完了したら、odbc データ ソース アドミニストレーターは、レジストリ情報を更新します。

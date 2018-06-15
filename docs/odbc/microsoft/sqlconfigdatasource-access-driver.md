---
title: SQLConfigDataSource (Access ドライバー) |Microsoft ドキュメント
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
- SQLConfigDataSource function [ODBC], Access Driver
- Access driver [ODBC], SQLConfigDataSource
ms.assetid: 1b152fb7-fa12-46b9-b168-006bb1355e77
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a792a34bc80ae7e25641aaea7aae88ed7b2349ac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904607"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLConfigDataSource**を追加するに使用される関数は、次の変更、または削除、データ ソースが動的に次のキーワードを使用します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|フィールドが並べ替えられたシーケンスです。<br /><br /> として同じオプションを設定**照合シーケンス**設定 ダイアログ ボックスをオンにします。|  
|COMPACT_DB|データベース ファイルのデータ圧縮を行います。 次の形式: COMPACT_DB = < path_name >< optionaL_sort_order >\<省略可能な暗号化のキーワード >。<br /><br /> COMPACT_DB キーワードを使用して、DSN キーワードを使用して、同じステートメントで、このドライバーは、DSN キーワードを無視します。 したがって、データベースを最適化して、DSN を指定することは、2 段階のプロセスです。|  
|CREATE_DB|データベース ファイルを作成します。 形式は次のとおり: CREATE_DB = < path_name >\<optional_sort 順序 >< optional_ENCRYPT キーワード >、ここで、パス名には、Microsoft Access データベースへの完全パス。 パス名が既存のデータベースを指定する場合、エラーが返されます。 並べ替え順序はセットとしての Microsoft Access のセットアップ ダイアログ ボックスで、作成 ボタンが押されたときに表示される新しいデータベース ダイアログ ボックスになります。 並べ替え順序が指定されていない場合は、[全般] が使用されます。<br /><br /> CREATE_DB キーワードを使用して、DSN キーワードを使用して、同じステートメントで、このドライバーは、DSN キーワードを無視します。 したがって、データベースを作成し、DSN を指定することは、2 段階のプロセスです。作成する Microsoft Access データベースのパス名には、1 つ以上のスペースが含まれている場合は、CREATE_DB キーワードを使用している場合、パス名全体囲む必要があります、二重引用符によって次の例に示すように。<br /><br /> "C:\PROGRAM files \common FILES files \ MyAccess.mdb"<br /><br /> "C:\PROGRAM FILES\Access2.mdb"<br /><br /> CREATE_DB=C:\TEMP\test.mdb (引用符は必要に応じて)|  
|CREATE_SYSDB|システム データベース ファイルを作成します。 次の形式: CREATE_SYSDB =\<パス名 >\<省略可能な並べ替え順序 > ここで、パス名は、Microsoft Access データベースへの完全パス。 パス名が既存のデータベースを指定する場合、エラーが返されます。 並べ替え順序になりますセットとしての**新しいデータベース** ダイアログ ボックスが表示されるときに、**作成**でボタンがクリックされた、 **ODBC Microsoft アクセスのセットアップ** ダイアログ ボックス。 並べ替え順序が指定されていない場合は、[全般] が使用されます。|  
|CREATE_V2DB|Microsoft Access 2.0 と互換性があるデータベース ファイルを作成します。 次の形式: CREATE_V2DB =\<パス名 >\<省略可能な並べ替え順序 > ここで、パス名は、Microsoft Access データベースへの完全パス。 パス名が既存のデータベースを指定する場合、エラーが返されます。 並べ替え順序はセットとしての Microsoft Access のセットアップ ダイアログ ボックスで、作成 ボタンが押されたときに表示される新しいデータベース ダイアログ ボックスになります。 並べ替え順序が指定されていない場合は、[全般] が使用されます。<br /><br /> CREATE_V2DB キーワードを使用して、DSN キーワードを使用して、同じステートメントで、このドライバーは、DSN キーワードを無視します。 したがって、データベースを作成し、DSN を指定することは、2 段階のプロセスです。<br /><br /> 作成する Microsoft Access データベースのパス名には、1 つ以上のスペースが含まれている場合は、CREATE_V2DB キーワードを使用している場合、パス名全体囲む必要があります、二重引用符によって次の例に示すように。<br /><br /> "C:\PROGRAM files \common FILES files \ MyAccess.mdb"<br /><br /> "C:\PROGRAM FILES\Access2.mdb"<br /><br /> CREATE_V2DB=C:\TEMP\test.mdb (引用符は必要に応じて)|  
|DBQ|データベース ファイルの名前です。<br /><br /> これと同じオプションを設定**データベース**設定 ダイアログ ボックスをオンにします。|  
|DEFAULTDIR|データベース ファイルへのパスの指定。|  
|DESCRIPTION|データ ソース内のデータの説明です。<br /><br /> 同じオプションを設定**説明**設定 ダイアログ ボックスをオンにします。|  
|DRIVER|ドライバー DLL にパス指定します。|  
|DRIVERID|ドライバーの整数 ID です。  25 (Microsoft Access)|  
|FIL|ファイルの種類の Microsoft Access MS アクセス|  
|IMPLICITCOMMITSYNC|Microsoft Access ドライバーが内部または暗黙的なコミットを非同期的に実行されるかどうかを判断します。 この値は"Yes"は、Microsoft Access ドライバーが完了する内部/暗黙のトランザクションでコミットを待機することを意味する初期設定されます。<br /><br /> このオプションの値は、結果を入念に考慮することがなくいない変更しなければなりません。 オプションの詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。<br /><br /> これと同じオプションを設定**ImplicitCommitSync**設定 ダイアログ ボックスをオンにします。|  
|MAXBUFFERSIZE|内部バッファーのサイズをキロバイト単位でディスク間でデータを転送する Microsoft Access で使用されます。 既定のバッファー サイズは、(2048 として表示) 2048 KB です。 任意の整数値を 256 で割り切れるを使用できます。 として同じオプションを設定**バッファー サイズ**設定 ダイアログ ボックスをオンにします。|  
|MAXSCANROWS|既存のデータに基づいて、列のデータ型を設定する場合にスキャンする行の数。<br /><br /> 16 ~ 1 の数値は、スキャンする行数を入力できます。 値の既定値は 8 です。0 に設定されている場合は、すべての行がスキャンされます。 (制限外の数値はエラーを返します。)<br /><br /> として同じオプションを設定**スキャンする行数**設定 ダイアログ ボックスをオンにします。|  
|PAGETIMEOUT|(ミリ秒単位) (使用しない場合)、ページが削除される前にバッファーに残っている時間の期間を指定します。 既定では 5 つの部分の 1/10 秒 (0.5 秒) です。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されることに注意してください。<br /><br /> 同じオプションを設定**ページのタイムアウト**設定 ダイアログ ボックスをオンにします。|  
|PWD|パスワード。|  
|READONLY|読み取り専用ファイルを作成する場合は TRUE読み取り専用ファイルを作成する場合は FALSE。<br /><br /> 同じオプションを設定**読み取り専用**設定 ダイアログ ボックスをオンにします。|  
|REPAIR_DB|コミット処理中に発生するエラーによって損傷しているデータベースを修復します。<br /><br /> REPAIR_DB キーワードを使用して、DSN キーワードを使用して、同じステートメントで、このドライバーは、DSN キーワードを無視します。 したがって、データベースを修復して、DSN を指定することは、2 段階のプロセスです。|  
|SYSTEMDB|Microsoft Access ドライバーでは、システム データベース ファイルへのパスを指定します。<br /><br /> これと同じオプションを設定**システム データベース**設定 ダイアログ ボックスをオンにします。|  
|スレッド|使用する、エンジンのバック グラウンド スレッドの数。 この値は、既定値は 3 が、変更することができます。<br /><br /> 同じオプションを設定**スレッド**設定 ダイアログ ボックスをオンにします。|  
|UID|ユーザー ID の名前は、Microsoft Access ドライバーのログインに使用します。|  
|USERCOMMITSYNC|Microsoft Access ドライバーがユーザー定義のトランザクションを非同期的に実行されるかどうかを判断します。 この値は"Yes"は、Microsoft Access ドライバーが完了するユーザー定義のトランザクションのコミットを待機することを意味する初期設定されます。<br /><br /> このオプションの値は、結果を入念に考慮することがなくいない変更しなければなりません。 オプションの詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。<br /><br /> これと同じオプションを設定**UserCommitSync**設定 ダイアログ ボックスをオンにします。|

---
title: "SQLConfigDataSource (Paradox ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLConfigDataSource
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9acd359d2d99531e3fe4092b3bd20f00e94622a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLConfigDataSource**を追加するに使用される関数は、次の変更、または削除、データ ソースが動的に次のキーワードを使用します。  
  
|Keyword|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|フィールドが並べ替えられたシーケンスです。<br /><br /> Paradox ドライバーを使用すると、シーケンスは、ASCII (既定値) をすることができます、国際化、スウェーデン語、フィンランド語、またはノルウェー語、デンマーク語。<br /><br /> として同じオプションを設定**照合シーケンス**設定 ダイアログ ボックスをオンにします。|  
|DBQ|データベース ファイルの名前です。<br /><br /> これと同じオプションを設定**データベース**設定 ダイアログ ボックスをオンにします。|  
|DEFAULTDIR|ディレクトリ パスの指定。|  
|DESCRIPTION|データ ソース内のデータの説明です。<br /><br /> 同じオプションを設定**説明**設定 ダイアログ ボックスをオンにします。|  
|DRIVER|ドライバー DLL にパス指定します。|  
|DRIVERID|ドライバーの整数 ID です。<br /><br /> 26 (paradox 3.x)<br /><br /> 282 (paradox 4.x)<br /><br /> 538 (paradox 5.x)|  
|排他的|データベースは (一度に 1 つだけのユーザーによってアクセス) 排他モードで開かれますまたはモード (一度に 1 つ以上のユーザーによってアクセス) を共有するかどうかを判断します。 (排他モード) を true または false (共有モード) を指定できます。<br /><br /> として同じオプションを設定**排他**設定 ダイアログ ボックスをオンにします。|  
|FIL|ファイルの種類 Paradox 3.x、Paradox 4.x、または Paradox 5.x|  
|ファイルの種類|テキスト ドライバー (テキスト) のファイルの種類。|  
|PAGETIMEOUT|部分ページ (使用しない場合) が削除される前にバッファーに残っている 1 秒の 1/10 で時間の期間を指定します。 既定値は 600 秒 (60 秒) の部分の 1/10。 このオプションは、ODBC ドライバーを使用するすべてのデータ ソースに適用されることに注意してください。<br /><br /> 同じオプションを設定**ページのタイムアウト**設定 ダイアログ ボックスをオンにします。|  
|PARADOXNETPATH|PDOXUSRS.net ファイルが含まれているために、ロックの paradox を含むディレクトリの完全なパス (Paradox 4 *。x*) または PARADOX.net ファイル (Paradox 5 *。x*)。 ディレクトリがこれらのファイルのいずれかにもない場合、Paradox ドライバーは 1 つを作成します。 これらのファイルについては、Paradox ドキュメントを参照してください。<br /><br /> ネットワーク ディレクトリを選択するには、Paradox ユーザー名を入力する必要があります。<br /><br /> として同じオプションを設定**ネットワーク ディレクトリの選択**設定 ダイアログ ボックスをオンにします。|  
|不正|Paradox ドライバー、ネットワーク アクセス Paradox データにアクセスするときに使用するスタイル: Paradox 3 のどちらか"3.x"です。*x*または Paradox 4 の"4.x".*x*または 5 *。x*です。 バージョンが Paradox 4 の場合は、"3.x"または"4.x"に設定できます。*x*または 5 *。x*以外の場合は、バージョンが Paradox 3 の場合*。x*スタイルが"3.x"にする必要があります。<br /><br /> として同じオプションを設定**Net スタイル**設定 ダイアログ ボックスをオンにします。|  
|PARADOXUSERNAME|Paradox ドライバーでは、Paradox ユーザー名。<br /><br /> 同じオプションを設定**ユーザー名**設定 ダイアログ ボックスをオンにします。|  
|PWD|パスワード。<br /><br /> これは省略可能なキーワードであり、ドライバーによって、ファイルに書き込むことはありません。 呼び出しで使用されている**SQLDriverConnect** Paradox ファイルのパスワードで保護されたとします。 テーブルを開くたびに使用するパスワードが有効になります。 接続文字列にパスワードが渡されない場合、そのテーブルのパスワードは確立されません。 テーブルがある別のパスワードは、同じセッションで、少なくとも 1 つ開くことができませんでない場合は、テーブルを結合することができます。|  
|READONLY|読み取り専用ファイルを作成する場合は TRUE読み取り専用ファイルを作成する場合は FALSE。<br /><br /> 同じオプションを設定**読み取り専用**設定 ダイアログ ボックスをオンにします。|  
|スレッド|使用する、エンジンのバック グラウンド スレッドの数。 この値は 3 であるため、変更できません。<br /><br /> 同じオプションを設定**スレッド**設定 ダイアログ ボックスをオンにします。|


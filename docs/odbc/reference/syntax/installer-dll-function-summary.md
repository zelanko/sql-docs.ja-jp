---
title: インストーラ DLL 関数の概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddaf20334a84833433961a49e17724d354945c5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298772"
---
# <a name="installer-dll-function-summary"></a>インストーラー DLL 関数の概要
次の表は、インストーラー DLL の関数を示しています。 各関数の構文とセマンティクスの詳細については、「インストーラー DLL API リファレンス」を[参照してください](../../../odbc/reference/syntax/installer-dll-api-reference-function.md)。  
  
|タスク|関数名|目的|  
|----------|-------------------|-------------|  
|ODBC のインストール|[ドライバー](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|ドライバー固有のセットアップ DLL を読み込みます。|  
||[ドライバーを取得します。](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|インストールされているドライバの一覧を返します。|  
||[ドライバのインストール](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|システム情報にドライバーを追加します。|  
||[ドライバー マネージャー](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|ドライバー マネージャーのターゲット ディレクトリを返します。|  
||[エラー](../../../odbc/reference/syntax/sqlinstallererror-function.md)|インストーラ関数のエラーまたはステータス情報を返します。|  
||[トランスレータ](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|システム情報にトランスレータを追加します。|  
||[エラー](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|ドライバまたはトランスレータのセットアップ ライブラリでエラーを報告できます。|  
||[ドライバーの削除](../../../odbc/reference/syntax/sqlremovedriver-function.md)|システム情報からドライバを削除します。|  
||[をクリックします。](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|システム情報から ODBC コア コンポーネントを削除します。|  
||[トランスレータを削除します。](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|システム情報からトランスレータを削除します。|  
|データ ソースの構成|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|ドライバー固有のセットアップ DLL を呼び出します。|  
||[データ ソースを作成します。](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|データ ソースを追加するためのダイアログ ボックスを表示します。|  
||[モード](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|DSN 値を示す Odbc.ini エントリがシステム情報内のどこにあるかを示すコンフィギュレーション モードを取得します。|  
||[文字列](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|システム情報に値を書き込みます。|  
||[トランスレータを取得します。](../../../odbc/reference/syntax/sqlgettranslator-function.md)|トランスレータを選択するためのダイアログ ボックスを表示します。|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|データ ソースとドライバを構成するダイアログ ボックスを表示します。|  
||[ファイルを読み取るDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|ファイル DSN から情報を読み取ります。|  
||[データ ソースを削除します。](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|既定のデータ ソースを削除します。|  
||[イニから削除します。](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|データ ソースを削除します。|  
||[設定モード](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|DSN 値を示す Odbc.ini エントリがシステム情報内のどこにあるかを示すコンフィギュレーション モードを設定します。|  
||[を指定します。](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|データ ソース名の長さと有効性を確認します。|  
||[を使用します。](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|データ ソースを追加します。|  
||[ファイルを書き込む](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|情報をファイル DSN に書き込みます。|  
||[文字列](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|システム情報から値を取得します。|

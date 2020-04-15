---
title: トラブルシューティング (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b035069c0be88d05a3aa5e17b96af991c27405
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303033"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>トラブルシューティング (Visual FoxPro ODBC ドライバー)
次のセクションでは、パフォーマンスを向上させる方法と、Visual FoxPro ODBC ドライバーの使用中に発生する可能性がある問題を解決する方法について説明します。  
  
## <a name="accessing-parameterized-views"></a>パラメータ化されたビューへのアクセス  
 ドライバーを使用して Visual FoxPro データベースのパラメーター化されたビューにアクセスすることはできません。 パラメーター化されたビューは、パラメーターに指定された値を使用して作成された WHERE 句の条件を満たすレコードにダウンロードされるレコードを制限する、ビューの SQL **SELECT**ステートメントに WHERE 句を作成します。 ドライバーは、ビューにパラメーターを渡すことをサポートしていないため、ドライバーを使用してパラメーター化されたビューにアクセスしようとすると失敗します。  
  
 パラメーター値は、実行時に指定することも、プログラムによってビューに渡すことができます。  
  
## <a name="accessing-remote-views"></a>リモート ビューへのアクセス  
 ドライバーを使用して Visual FoxPro データベース内のリモート ビューにアクセスすることはできません。 リモートビューは、FoxPro 以外のデータまたは FoxPro と非 FoxPro 以外のデータの組み合わせのいずれかにアクセスするビューです。 リモート ビューにアクセスするには、ビジュアル フォックスプロを使用します。  
  
## <a name="deleting-records"></a>レコードの削除  
 ドライバを使用してレコードを削除対象としてマークすることはできますが、データベースからレコードを完全に削除することはできません。 テーブルからレコードを完全に削除するには、Visual FoxPro を使用します。  
  
## <a name="increasing-performance-using-background-fetching"></a>バックグラウンド・フェッチを使用したパフォーマンスの向上  
 ドライバーのバックグラウンドフェッチ機能を使用して、大きいフェッチのパフォーマンスを向上させることができます。 バックグラウンドでフェッチする場合は、個別のスレッドを使用して、特定のデータ ソースから要求されたデータをフェッチします。  
  
 データ ソースのバックグラウンドフェッチは、次のいずれかの方法で使用できます。  
  
-   [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)で[**バックグラウンドでデータをフェッチ**] チェックボックスをオンにします。  
  
-   接続文字列で BackgroundFetch 属性キーワードを使用します。  
  
 接続文字列属性キーワードの詳細については、「[接続文字列の使用](../../odbc/microsoft/using-connection-strings.md)」を参照してください。  
  
## <a name="updating-multitiered-views"></a>多層ビューの更新  
 多層ビューは、ベース テーブルではなく、1 つまたは複数のビューに基づくビューです。 多層ビューでデータを更新すると、更新は、最上位のビューが基になるビューに 1 つのレベルだけ下がります。ベース テーブルは更新されません。  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>ストアド プロシージャでのデータ定義言語 (DDL) の使用  
 ビジュアル FoxPro ストアド プロシージャでは、テーブルの作成やテーブルの変更などの DDL を使用することはできません。  
  
 ストアド プロシージャで使用できる言語の詳細については、「[ルール、トリガ、既定値、およびストアド プロシージャのサポート](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md)」を参照してください。  
  
## <a name="using-positioned-updates"></a>位置指定更新の使用  
 ドライバーは、位置指定更新をサポートしていません。 SQL WHERE 句を使用して、更新する行を指定します。  
  
## <a name="using-the-set-ansi-command"></a>SET ANSI コマンドの使用  
 Visual FoxPro 開発者の場合は、ドライバの SET ANSI の既定の設定は ON であり、Visual FoxPro の既定の設定はオフになっていることに注意してください。 SET ANSI の既定の ON 設定では、Visual FoxPro データ ソースは、通常は正確な比較を実行する他の ODBC データ ソースと一貫して動作します。 デフォルト設定は変更できます。 詳細については、「 [ANSI を設定](../../odbc/microsoft/set-ansi-command.md)する 」を参照してください。

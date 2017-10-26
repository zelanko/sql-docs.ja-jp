---
title: "トラブルシューティング (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
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
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3db2f795910c0ee331ad77903b12201f365784e6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>トラブルシューティング (Visual FoxPro ODBC ドライバー)
次のセクションでは、パフォーマンスが向上し、Visual FoxPro ODBC ドライバーを使用しているときに発生する可能性の問題を解決する方法について説明します。  
  
## <a name="accessing-parameterized-views"></a>パラメーター化されたビューへのアクセス  
 パラメーター化されたデータベースのビューの Visual FoxPro、ドライバーを使用してアクセスすることはできません。 パラメーター化されたビュー、ビューの SQL の WHERE 句を作成する**選択**レコードを制限するステートメントがパラメーターに指定された値を使用して構築された WHERE 句の条件に一致するレコードにダウンロードします。 ドライバーがビューにパラメーターの引き渡しをサポートしていないため、ドライバーを使用してパラメーター化されたビューにアクセスする試行は失敗します。  
  
 パラメーターの値は、実行時に提供またはビューにプログラムで渡されることがことができます。  
  
## <a name="accessing-remote-views"></a>リモート ビューへのアクセス  
 リモート データベースのビューの Visual FoxPro、ドライバーを使用してアクセスすることはできません。 リモートのビューは、非 FoxPro データまたは FoxPro と FoxPro 以外のデータの組み合わせのいずれかにアクセスするビューです。 リモートのビューにアクセスするには、Visual FoxPro を使用します。  
  
## <a name="deleting-records"></a>レコードを削除します。  
 ドライバーを使用して削除対象のレコードをマークすることができますが、データベースからレコードを完全に削除することはできません。 テーブルからレコードを完全に削除するには、Visual FoxPro を使用します。  
  
## <a name="increasing-performance-using-background-fetching"></a>バック グラウンドでフェッチを使用してパフォーマンスの向上  
 ドライバーの機能をフェッチするバック グラウンドを使用して大規模なフェッチでパフォーマンスが向上します。 バック グラウンドのフェッチでは、別のスレッドを使用して特定のデータ ソースから要求されたデータを取り出します。  
  
 バック グラウンドで、次の方法のいずれかのデータ ソースのフェッチを採用することができます。  
  
-   チェック、**バック グラウンドでデータをフェッチ**チェック ボックス、 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)です。  
  
-   接続文字列で BackgroundFetch 属性キーワードを使用します。  
  
 接続文字列キーワードの属性については、次を参照してください。[接続文字列を使用して](../../odbc/microsoft/using-connection-strings.md)です。  
  
## <a name="updating-multitiered-views"></a>多階層ビューの更新  
 多層ビューは、ベース テーブルではなく 1 つまたは複数のビューに基づいてビューです。 最上位のビューの基になる; ビューに、更新プログラムが下のレベルを 1 つだけにするには、移動多層ビューでデータを更新するときにベース テーブルは更新されません。  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>ストアド プロシージャでのデータ定義言語 (DDL) の使用  
 Visual FoxPro がストアド プロシージャで CREATE TABLE または ALTER TABLE などの DDL を使用することはできません。  
  
 ストアド プロシージャで使用できる言語については、次を参照してください。[規則、トリガー、既定値、およびストアド プロシージャのサポート](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md)です。  
  
## <a name="using-positioned-updates"></a>位置指定更新を使用します。  
 ドライバーは、位置指定更新をサポートしていません。 SQL の WHERE 句を使用して、更新する行を識別します。  
  
## <a name="using-the-set-ansi-command"></a>SET ANSI コマンドの使用  
 Visual FoxPro 開発者でない場合に、ANSI の設定の既定の設定では、Visual FoxPro の OFF の既定の設定とは異なり、ドライバーの ON が、注意してください。 既定の設定の ANSI の設定には、通常正確な比較を実行する他の ODBC データ ソースと一貫して動作する Visual FoxPro データ ソースができるようにします。 既定の設定を変更することができます。 詳細については、次を参照してください。[設定の ANSI](../../odbc/microsoft/set-ansi-command.md)です。


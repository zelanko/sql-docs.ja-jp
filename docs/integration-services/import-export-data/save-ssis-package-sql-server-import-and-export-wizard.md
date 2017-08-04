---
title: "SSIS パッケージ (SQL Server インポートおよびエクスポート ウィザード) を保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
caps.latest.revision: 64
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 6ebbab742350e6874b86213c1fbf516e095a1e9a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)
  指定した場合、**パッケージの実行を保存して**を SQL Server Integration Services (SSIS) パッケージとして、その設定を保存するページを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザードの番組**SSIS パッケージの保存**です。 このページでは、ウィザードによって作成されたパッケージを保存するための追加のオプションを指定します。  

**[SSIS パッケージの保存]** ページに表示されるオプションは、SQL Server またはファイル システムにパッケージを保存するために **[パッケージの保存および実行]** ページで以前に行った選択によって異なります。 **[パッケージの保存および実行]** ページについては、「 [Save and Run Package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)」 ([パッケージの保存および実行]) を参照してください。
 
**パッケージとは** ウィザードは SQL Server Integration Services (SSIS) を使用してデータをコピーします。 SSIS での基本単位はパッケージです。 ウィザードのページを進みながらオプションを指定すると、SSIS パッケージがメモリに作成されます。

## <a name="screen-shot---common-options"></a>スクリーン ショットの一般的なオプション
次のスクリーン ショットの最初の部分を示しています、 **SSIS パッケージの保存**ウィザードのページです。 ページの残りの部分では、可変個の選択したパッケージの移行先に依存するオプションがあります。

![パッケージの一般的なオプションを保存します。](../../integration-services/import-export-data/media/save-package-common-options.png)

## <a name="provide-a-name-and-description-for-the-package"></a>パッケージの名前と説明を指定します。  
 **名前**  
 パッケージの一意な名前を指定します。  
  
 **説明**  
 パッケージの説明を指定します。 パッケージを見るだけでその内容がわかり、保守が容易になるように、パッケージの目的について記述することをお勧めします。  
  
 **ターゲット**  
 パッケージに対して以前に指定した保存先です ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル システム)。 別の保存先にパッケージを保存する場合は、 **[パッケージの保存および実行]** ページに戻ります。

## <a name="screen-shot---save-the-package-in-sql-server"></a>スクリーン ショット - SQL Server にパッケージを保存する

 次のスクリーン ショット、 **SSIS パッケージの保存**を選択した場合、ウィザードのページ、 **SQL Server**  オプションを選択、**パッケージの実行を保存して**ページ。 
  
![インポートおよびエクスポート ウィザードの [SSIS パッケージ] ページを保存](../../integration-services/import-export-data/media/save-package2.png "インポートおよびエクスポート ウィザードのページを SSIS パッケージの保存")  

## <a name="options-to-specify-target--sql-server"></a>指定するオプション (ターゲット = SQL Server) 

 > [!NOTE]
 > ウィザードでパッケージの保存、 **msdb**データベースに格納されて、 **sysssispackages**テーブル。 このオプションでは**いない**SSIS カタログ データベース (SSISDB) にパッケージを保存します。  
 
 **サーバー名**  
 保存先のサーバー名を入力または選択します。  
   
 **Windows 認証を使用する**  
Windows 統合認証を使用してサーバーに接続します。 これは、推奨される認証方法です。  
  
 **SQL Server 認証を使用する**  
SQL Server 認証を使用してサーバーに接続します。  
  
 **ユーザー名**  
SQL Server 認証を指定した場合は、ユーザー名を入力します。  
  
 **Password**  
SQL Server 認証を指定した場合は、パスワードを入力します。  
    
## <a name="screen-shot---save-the-package-in-the-file-system"></a>スクリーン ショット - ファイル システムにパッケージを保存する
 
次のスクリーン ショット、 **SSIS パッケージの保存**を選択した場合、ウィザードのページ、**ファイル システム** オプションを選択、**パッケージの実行を保存して**ページ。 
  
![インポートおよびエクスポート ウィザードの [SSIS パッケージ] ページを保存](../../integration-services/import-export-data/media/save-package1.png "インポートおよびエクスポート ウィザードのページを SSIS パッケージの保存")  

## <a name="options-to-specify-target--file-system"></a>指定するオプション (ターゲット = ファイル システム)

 **[ファイル名]**  
 コピー先ファイルのパスとファイル名を入力またはを使用して、**参照**を変換先を選択します。  
  
> [!TIP]
> 必ずデータを入力するかを参照して、コピー先フォルダーを指定してください。 のみパスを含まないファイル名を入力すると、ウィザードでパッケージを保存する場所がわからない。 また、ウィザードはユーザーがファイル保存権限を持っていない場所にパッケージを保存しようとして、エラーが発生する可能性があります。  
>   
>  パッケージ ファイルの保存場所を忘れないでください。  
  
 **参照**  
 変換先ファイルのパスを選択する必要に応じて、参照、**パッケージの保存** ダイアログ ボックス。  

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>パッケージを保存するためのオプションの 2 つのページについて  
 **[SSIS パッケージの保存]** ページは、SSIS パッケージを保存するためのオプションを選択する 2 つのページの 1 つです。  
  
-   前の **[パッケージの保存および実行]**ページでは、SQL Server またはファイルのどちらにパッケージを保存するかを選択します。 保存されたパッケージのセキュリティ設定も選択します。 **[パッケージの保存および実行]** ページについては、「 [Save and Run Package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md)」 ([パッケージの保存および実行]) を参照してください。  
  
-   このページでは、パッケージの名前および保存場所に関する詳細情報を指定します。  
 
## <a name="run-the-saved-package-again-later"></a>保存したパッケージを後で再び実行する  
 保存したパッケージを後で再び実行する方法については、以下のトピックを参照してください。  
  
-   使い慣れたユーティリティ プログラムを使用してパッケージを実行するには、「[パッケージ実行ユーティリティ (DtExecUI) の UI リファレンス](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md)」を参照してください。  
  
-   コマンドラインまたはバッチ ファイルからパッケージを実行するには、「 [dtexec ユーティリティ](../../integration-services/packages/dtexec-utility.md)」を参照してください。  
  
-   SQL Server の **msdb** データベースにパッケージを保存した場合は、Integration Services サービスに接続します。 次に、SQL Server Management Studio のオブジェクト エクスプローラーで **[格納済みパッケージ]、[MSDB]**に移動し、パッケージを右クリックして、 **[パッケージの実行]**を選択します。

-   ファイル システムにパッケージを保存した場合、開発環境でパッケージを実行するには、「 [Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md) 」を参照してください。 パッケージを開いて実行する前に、パッケージを Integration Services プロジェクトに追加する必要があります。  

## <a name="customize-the-saved-package"></a>保存されたパッケージをカスタマイズする  
 保存されたパッケージをカスタマイズする方法については、「[Integration Services (SSIS) パッケージ](../../integration-services/integration-services-ssis-packages.md)」を参照してください。  
  
## <a name="whats-next"></a>次の操作  
 パッケージ保存の追加オプションを指定した後、次のページは **[ウィザードの完了]**です。 このページでは、ウィザードで選択した内容を確認し、操作を開始します。 詳細については、「 [[ウィザードの完了] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)」を参照してください。  
 
## <a name="see-also"></a>参照  
[パッケージを保存する](../../integration-services/save-packages.md)  
[Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
 


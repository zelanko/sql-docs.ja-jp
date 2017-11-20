---
title: "保存し、実行パッケージ (SQL Server インポートおよびエクスポート ウィザード) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/16/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 69
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f5acdf3ae4f27685fce7aab56aab423044491ee1
ms.openlocfilehash: 40b8677cddf363e8789a2fc15b1c2aab5f49f58c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="save-and-run-package-sql-server-import-and-export-wizard"></a>[パッケージの保存および実行]\ (SQL Server インポートおよびエクスポート ウィザード)
  データ ソースと宛先を指定して構成すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードによって **[パッケージの保存および実行]**が表示されます。 このページでは、コピー操作をすぐに実行するかどうかを指定します。 構成によっては、またことができますと設定を保存する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) パッケージをカスタマイズして、後で再利用します。
  
**パッケージとは** ウィザードは SQL Server Integration Services (SSIS) を使用してデータをコピーします。 SSIS での基本単位はパッケージです。 ウィザードのページを進みながらオプションを指定すると、SSIS パッケージがメモリに作成されます。
  
## <a name="screen-shot-of-the-save-and-run-package-page"></a>[パッケージの保存および実行] ページのスクリーン ショット  
次のスクリーン ショットは、ウィザードの **[パッケージの保存および実行]** ページを示しています。 
   
![保存し、インポートおよびエクスポート ウィザードの [パッケージ] ページの実行](../../integration-services/import-export-data/media/save-and-run.png "保存し、インポートおよびエクスポート ウィザードの [パッケージ] ページの実行") 
  
## <a name="run-and-save-the-package"></a>パッケージの実行および保存 
 次に進むには、次の 2 つのオプションから少なくとも 1 つを選択する必要があります。  
  
 **Run immediately**  
 インポートし、データのエクスポートをすぐにこのオプションを選択します。 既定では、このチェック ボックスが選択されているし、操作がすぐに実行されます。
  
 **SSIS パッケージの保存**  
 設定は、SSIS パッケージとして保存します。 後から、必要に応じてパッケージをカスタマイズして再実行できます。 パッケージの保存を選択すると、次のページ **[SSIS パッケージの保存]**にさらにオプションが表示されます。
 
パッケージを保存するオプションを選択できるのは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition 以上のエディションをインストールしている場合のみです。   
  
> [!NOTE]
> 場合は、ウィザードを終了、操作を実行する前に、操作を停止するには、実行が完了した、パッケージは保存されません、選択した場合でも、 **SSIS パッケージの保存**チェック ボックスをオンします。  

### <a name="if-you-started-the-wizard-from-visual-studio"></a>Visual Studio からウィザードを起動した場合
Visual Studio と SQL Server Data Tools (SSDT) で Integration Services プロジェクトからは、ウィザードを起動します。 場合
-   ことはできません**実行**パッケージの作成ウィザードを終了した後になるまでです。 Visual Studio からそのパッケージを実行できます。
-   ウィザード**保存**ウィザードを起動した Integration Services プロジェクトのパッケージです。

## <a name="specify-options-for-saving-the-package"></a>パッケージを保存する場合のオプションを指定する
**SQL Server**  
 内の SQL Server でパッケージを保存するには、このオプションを選択、 **msdb**データベースに格納されて、 **sysssispackages**テーブル。
 
> [!IMPORTANT]
> このオプションでは、SSIS カタログ データベース (SSISDB) にパッケージを保存できません。  

 対象サーバーを選択し、サーバーに接続するための資格情報を次のページ **[SSIS パッケージの保存]**で指定します。 詳細については、「 [[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 **ファイル システム**  
 ファイルとしてパッケージを保存するには、このオプションを選択、 **.dtsx**拡張機能です。  
  
 パッケージの対象フォルダーとファイル名を、次のページ **[SSIS パッケージの保存]**で選択します。 詳細については、「 [[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)」を参照してください。  
 
 ## <a name="specify-the-package-protection-level"></a>パッケージの保護レベルを指定する
 **パッケージの保護レベル**  
 パッケージのデータを保護するために、リストから保護レベルを選択します。  
  
 保護レベルによって、パッケージ保護の方法、パスワードまたはユーザー キー、適用範囲が決定されます。 保護対象には、すべてのデータを含めることも機密データのみを含めることもできます。 使用可能なオプションの詳細については、「 [パッケージ内の機微なデータへのアクセス制御](../../integration-services/security/access-control-for-sensitive-data-in-packages.md)」を参照してください。  
  
 **パスワード**  
 パスワードを入力します。  
  
 **パスワードの再入力**  
 パスワードを再度入力します。  
  
> [!NOTE]
> パスワード オプションがある場合にのみ指定、**パッケージの保護レベル**を必要とする、パスワードは、いずれかを指定する場合**パスワードを使用して機密データを暗号化**または**パスワードを持つすべてのデータを暗号化**です。  

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>パッケージを保存するためのオプションの 2 つのページについて  
 **[パッケージの保存および実行]** ページは、SSIS パッケージを保存するためのオプションを選択する 2 つのページの 1 つです。  
  
-   現在のページで、SQL Server またはファイルのどちらにパッケージを保存するかを選択します。 保存されたパッケージのセキュリティ設定も選択します。  
  
-   次に、 **[SSIS パッケージの保存]** ページで、パッケージの名前および保存場所に関する詳細情報を指定します。 詳細については、「 [[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 これらのオプションを使用できるのは、このページで **[SSIS パッケージの保存]** オプションを選択する場合のみです。  
  
## <a name="whats-next"></a>次の操作  
 コピー操作をすぐに実行するかどうかと、パッケージを保存するかどうかを指定した場合は、選択したオプションに応じて次のページが変わります。  
  
-   パッケージをすぐに実行することを選択した場合、次のページは **[ウィザードの完了]**です。 このページでは、ウィザードで選択した内容を確認し、コピー操作を開始します。 詳細については、「 [[ウィザードの完了] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/complete-the-wizard-sql-server-import-and-export-wizard.md)」を参照してください。  
  
-   パッケージを保存するオプションを選択した場合、次のページは **[SSIS パッケージの保存]**です。 このページでは、パッケージを保存するための追加オプションを指定します。 (パッケージを保存すると、その後のページは **[ウィザードの完了]** になります。)詳細については、「[[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[パッケージを保存する](../../integration-services/save-packages.md)  
[Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
[インポートおよびエクスポート ウィザードのこの簡単な例の概要します。](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

  



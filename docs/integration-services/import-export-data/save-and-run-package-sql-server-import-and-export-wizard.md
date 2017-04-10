---
title: "[パッケージの保存および実行] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: ""
ms.date: "02/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.saveschedule.f1"
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 69
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 65
---
# [パッケージの保存および実行] (SQL Server インポートおよびエクスポート ウィザード)
  データ ソースと宛先を指定して構成すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードによって **[パッケージの保存および実行]** が表示されます。 このページでは、コピー操作をすぐに実行するかどうかを指定します。 構成によっては、ウィザードによって作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) パッケージを保存して、それをカスタマイズし、後から再利用することができます。
  
**パッケージとは** ウィザードは SQL Server Integration Services (SSIS) を使用してデータをコピーします。 SSIS での基本単位はパッケージです。 ウィザードのページを進みながらオプションを指定すると、SSIS パッケージがメモリに作成されます。
  
## <a name="screen-shot-of-the-save-and-run-package-page"></a>[パッケージの保存および実行] ページのスクリーン ショット  
次のスクリーン ショットは、ウィザードの **[パッケージの保存および実行]** ページを示しています。 
   
![Save and run package page of the Import and Export Wizard](../../integration-services/import-export-data/media/save-and-run.png "Save and run package page of the Import and Export Wizard") 
  
## <a name="run-and-save-the-package"></a>パッケージの実行および保存 
 次に進むには、次の 2 つのオプションから少なくとも 1 つを選択する必要があります。  
  
 **すぐに実行する**  
 このオプションを選択すると、すぐにパッケージを実行します。  
  
 **SSIS パッケージの保存**  
 パッケージを保存します。 後から、必要に応じてパッケージをカスタマイズして再実行できます。 パッケージの保存を選択すると、次のページ **[SSIS パッケージの保存]** にさらにオプションが表示されます。 パッケージを保存するオプションを選択できるのは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition 以上のエディションをインストールしている場合のみです。   
  
> [!NOTE] ウィザードを終了し、パッケージを実行してからその実行が終了する前に自分で停止した場合は、このページの **[保存]** チェック ボックスをオンにしていても、パッケージは保存されません。  
  
## <a name="specify-options-for-saving-the-package"></a>パッケージを保存する場合のオプションを指定する
**SQL Server**  
 このオプションを選択して、**msdb** データベースの **sysssispackages** テーブルにパッケージを保存します。
 
> [!NOTE] このオプションでは、SSIS カタログ データベース (SSISDB) にパッケージを保存できません。  

 対象サーバーを選択し、サーバーに接続するための資格情報を次のページ **[SSIS パッケージの保存]** で指定します。 詳細については、「[[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」を参照してください。  
  
 **ファイル システム**  
 このオプションを選択して、**.dtsx** 拡張子を持つファイルとしてパッケージを保存します。  
  
 パッケージの対象フォルダーとファイル名を、次のページ **[SSIS パッケージの保存]** で選択します。 詳細については、「[[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」を参照してください。  
 
 ## <a name="specify-the-package-protection-level"></a>パッケージの保護レベルを指定する
 **パッケージの保護レベル**  
 パッケージのデータを保護するために、リストから保護レベルを選択します。  
  
 保護レベルによって、パッケージ保護の方法、パスワードまたはユーザー キー、適用範囲が決定されます。 保護対象には、すべてのデータを含めることも機密データのみを含めることもできます。 使用可能なオプションの詳細については、「[パッケージ内の機微なデータへのアクセス制御](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)」を参照してください。  
  
 **パスワード**  
 パスワードを入力します。  
  
 **パスワードの再入力**  
 パスワードを再度入力します。  
  
> [!NOTE] このパスワード オプションは、パスワードが必要な **[パッケージの保護レベル]** を指定した場合 (つまり、**[機微なデータをパスワードで暗号化する]** または **[すべてのデータをパスワードで暗号化する]**) にのみ使用できます。  

## <a name="can-i-run-and-save-the-package"></a>パッケージの実行および保存
 ウィザードの開始に使用した方法によって、ウィザードで作成されるパッケージを実行して保存できるかどうかが決まります。 ウィザードのこのページで **[実行]** オプションまたは **[保存]** オプションが無効な場合があります。
 
|ウィザードの開始方法|パッケージを実行できるか|パッケージを保存できるか|
|------------------------|------------------------|-------------------------|
|[スタート] メニュー、コマンド プロンプト、または SQL Server Management Studio からウィザードを開始します。|**[すぐに実行する]** チェック ボックスをオンにすると、ウィザードの終了時にパッケージをすぐに実行できます。 既定では、このチェック ボックスがオンになり、パッケージはすぐに実行されます。|SQL Server Standard Edition 以上をインストールしている場合は、オプションを使用してパッケージを保存できます。|
|SQL Server Data Tools (SSDT) の Integration Services プロジェクトからウィザードを開始します。|ウィザードを終了しないとパッケージを実行できません。 その後、SQL Server Data Tools でパッケージを実行できます。|ウィザードを開始した Integration Services プロジェクトにパッケージが保存されます。|

## <a name="about-the-two-pages-of-options-for-saving-the-package"></a>パッケージを保存するためのオプションの 2 つのページについて  
 **[パッケージの保存および実行]** ページは、SSIS パッケージを保存するためのオプションを選択する 2 つのページの 1 つです。  
  
-   現在のページで、SQL Server またはファイルのどちらにパッケージを保存するかを選択します。 保存されたパッケージのセキュリティ設定も選択します。  
  
-   次に、**[SSIS パッケージの保存]**ページで、パッケージの名前および保存場所に関する詳細情報を指定します。 詳細については、「[[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」を参照してください。  
  
 これらのオプションを使用できるのは、このページで **[SSIS パッケージの保存]** オプションを選択する場合のみです。  
  
## <a name="whats-next"></a>次の操作  
 コピー操作をすぐに実行するかどうかと、パッケージを保存するかどうかを指定した場合は、選択したオプションに応じて次のページが変わります。  
  
-   パッケージをすぐに実行することを選択した場合、次のページは **[ウィザードの完了]** です。 このページでは、ウィザードで選択した内容を確認し、コピー操作を開始します。 詳細については、「[[ウィザードの完了] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Complete%20the%20Wizard%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」を参照してください。  
  
-   パッケージを保存するオプションを選択した場合、次のページは **[SSIS パッケージの保存]** です。 このページでは、パッケージを保存するための追加オプションを指定します。 (パッケージを保存すると、その後のページは **[ウィザードの完了]** になります。)詳細については、「[[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード)](../Topic/Save%20SSIS%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[パッケージを保存する](../../integration-services/save-packages.md)  
[Integration Services (SSIS) パッケージの実行](../../integration-services/packages/run-integration-services-ssis-packages.md)  
[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)
 
  

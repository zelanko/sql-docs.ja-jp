---
title: "デジタル証明書を使用してパッケージに署名する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デジタル署名 [Integration Services]"
  - "パッケージの署名 [Integration Services]"
  - "署名 [Integration Services]"
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
caps.latest.revision: 60
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 60
---
# デジタル証明書を使用してパッケージに署名する
  このトピックでは、デジタル証明書を使用して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージに署名する方法について説明します。 デジタル署名を他の設定と共に使用して、有効でないパッケージの読み込みや実行を防ぐことができます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージに署名する前に、次のタスクを実行する必要があります。  
  
-   証明書と関連付ける秘密キーを作成または取得して、この秘密キーをローカル コンピューターに格納します。  
  
-   信頼できる証明機関からコード署名用の証明書を入手します。 証明書を取得または作成するには、次のいずれかの方法を使用できます。  
  
    -   証明書を発行する公的な商用証明機関から証明書を入手します。  
  
    -   組織が証明書を内部的に発行できるようにする証明書サーバーから証明書を入手します。 証明書の署名に使用されるルート証明書を、**[信頼されたルート証明機関]** ストアに追加する必要があります。 ルート証明書を追加するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール (MMC) の証明書スナップインを使用します。 詳細については、MSDN ライブラリの「[証明書サービス](http://go.microsoft.com/fwlink/?LinkId=100755)」を参照してください。  
  
    -   テスト目的でのみ独自の証明書を作成します。 証明書作成ツール (Makecert.exe) は、テスト目的で X.509 証明書を生成します。 詳細については、MSDN ライブラリの「[証明書作成ツール (Makecert.exe)](http://go.microsoft.com/fwlink/?LinkId=100756)」を参照してください。  
  
     証明書の詳細については、証明書スナップインのオンライン ヘルプを参照してください。 デジタル アセットの署名方法の詳細については、MSDN ライブラリの「[Authenticode を使用したコードの署名と検証](http://go.microsoft.com/fwlink/?LinkId=78100)」を参照してください。  
  
-   証明書がコードの署名用に有効になっていることを確認します。 証明書がコードの署名用に有効になっているかどうかを判断するには、証明書スナップインで証明書のプロパティを確認します。  
  
-   個人ストアに証明書を格納します。  
  
 上記のタスクが完了したら、次の手順に従ってパッケージに署名できます。  
  
### パッケージに署名するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、署名するパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで **[SSIS]** メニューの **[デジタル署名]** をクリックします。  
  
4.  **[デジタル署名]** ダイアログ ボックスで、**[署名]** をクリックします。  
  
5.  **[証明書の選択]** ダイアログ ボックスで、証明書を選択します。  
  
6.  必要に応じて、**[証明書の表示]** をクリックして証明書の情報を表示します。  
  
7.  **[OK]** をクリックして、**[証明書の選択]** ダイアログ ボックスを閉じます。  
  
8.  **[OK]** をクリックして、**[デジタル署名]** ダイアログ ボックスを閉じます。  
  
9. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
     パッケージは署名されましたが、パッケージを読み込む前にデジタル署名を確認するように、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を構成する必要があります。 詳細については、「[デジタル署名を使用してパッケージのソースを特定する](../../integration-services/packages/identify-the-source-of-packages-with-digital-signatures.md)」を参照してください。  
  
## 参照  
 [セキュリティの概要 (Integration Services)](../../integration-services/security/security-overview-integration-services.md)  
  
  
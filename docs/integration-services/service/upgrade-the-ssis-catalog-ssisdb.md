---
title: "SSIS カタログ (SSISDB) のアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.dbupgradewizard.f1"
ms.assetid: 170c3dc9-f5bf-4599-ae56-d24a620f23e8
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# SSIS カタログ (SSISDB) のアップグレード
  データベースが SQL Server インスタンスの現在のバージョンよりも古い場合、SSISDB アップグレード ウィザードを実行して、SSIS カタログ データベース (SSISDB) をアップグレードしてください。 この状況は、次のいずれかの条件が該当した場合に発生します。  
  
-   古いバージョンの SQL Server からデータベースを復元した場合。  
  
-   SQL Server インスタンスをアップグレードする前に Always On 可用性グループからデータベースを削除しなかった場合。 この場合、データベースは自動アップグレードされません。 詳細については、「 [Upgrading SSISDB in an availability group](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade)」を参照してください。  
  
 このウィザードでは、ローカル サーバー インスタンス上のデータベースのみをアップグレードできます。  
  
## SSISDB アップグレード ウィザードを実行して SSIS カタログ (SSISDB) をアップグレードする  
  
1.  SSIS カタログ データベース (SSISDB) をバックアップします。  
  
2.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でローカル サーバーを展開し、 **[Integration Services カタログ]**を展開します。  
  
3.  **[SSISDB]** を右クリックして **[データベースのアップグレード]** を選択し、SSISDB アップグレード ウィザードを起動します。  
  
     ![Launch the SSISDB upgrade wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-1.png "Launch the SSISDB upgrade wizard")  
  
4.  **[インスタンスの選択]** ページで、ローカル サーバー上の SQL Server インスタンスを選択します。  
  
    > [!IMPORTANT]  
    >  このウィザードでは、ローカル サーバー インスタンス上のデータベースのみをアップグレードできます。  
  
     ウィザードを実行する前に SSISDB データベースをバックアップしたことを示すために、チェック ボックスをオンにします。  
  
     ![Select the server in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-2.png "Select the server in the SSISDB Upgrade Wizard")  
  
5.  **[アップグレード]** を選択して SSIS カタログ データベースをアップグレードします。  
  
6.  **[結果]** ページで結果を確認します。  
  
     ![Review the results in the SSISDB Upgrade Wizard](../../integration-services/service/media/ssisdb-upgrade-wizard-3.png "Review the results in the SSISDB Upgrade Wizard")  
  
  
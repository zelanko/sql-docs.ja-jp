---
title: Integration Services Service | のプロパティを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 29e57da658b97d4ed3d9867dfee51644f0af9ddc
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963162"
---
# <a name="set-the-properties-of-the-integration-services-service"></a>Integration Services サービスのプロパティを設定する
    
> [!IMPORTANT]  
>  このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]でパッケージを管理および監視します。 を最初にインストールすると [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが開始され、サービスのスタートアップの種類が [自動] に設定されます。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスをインストールしたら、SQL Server 構成マネージャーまたはサービス MMC スナップインを使用してサービスのプロパティを設定できます。  
  
 パッケージを格納および管理する場所など、サービスのその他の重要な機能を構成するには、サービスの構成ファイルを変更する必要があります。 詳細については、「 [Integration Services サービスの構成 (SSIS サービス)](service/integration-services-service-ssis-service.md)との互換性を維持するために、このサービスをサポートしています。  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a>SQL Server 構成マネージャーを使用して Integration Services サービスのプロパティを設定するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** 、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。  
  
2.  **[SQL Server 構成マネージャー]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。次に、 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  [ **SQL Server Integration Services のプロパティ**] ダイアログボックスでは、次の操作を実行できます。  
  
    -   **[ログオン]** タブをクリックして、アカウント名などのログオン情報を表示します。  
  
    -   **[サービス]** タブをクリックして、ホスト コンピューター名などのサービスに関する情報を表示し、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスの開始モードを指定します。  
  
        > [!NOTE]  
        >  **[詳細設定]** タブに、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスに関する情報は表示されません。  
  
4.  **[OK]** をクリックします。  
  
5.  **[ファイル]** メニューの **[終了]** をクリックして **[SQL Server 構成マネージャー]** スナップインを終了します。  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a>[サービス] を使用して Integration Services サービスのプロパティを設定するには  
  
1.  **[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]**、カテゴリの表示を使用している場合は **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。  
  
2.  [**サービス**] をクリックします。  
  
3.  **[サービス]** スナップインで、サービスの一覧から **[SQL Server Integration Services]** を探します。 **[SQL Server Integration Services]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  **[SQL Server Integration Services のプロパティ]** ダイアログ ボックスでは、次の操作を行うことができます。  
  
    -   [**全般**] タブをクリックします。サービスを有効にするには、手動または自動のスタートアップの種類を選択します。 サービスを無効にするには、 **[スタートアップの種類]** ボックスで [無効] を選択します。 [無効] を選択しても、実行中のサービスは停止されません。  
  
         サービスが既に有効になっている場合は、 **[停止]** をクリックしてサービスを停止したり、 **[開始]** をクリックしてサービスを開始したりできます。  
  
    -   **[ログオン]** タブをクリックして、ログオン情報を表示または編集します。  
  
    -   **[復旧]** タブをクリックして、サービスが失敗した場合のコンピューターの既定の応答を表示します。 これらのオプションは、環境に合わせて変更できます。  
  
    -   **[依存関係]** タブをクリックして、依存サービスの一覧を表示します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスは、依存関係を持ちません。  
  
5.  **[OK]** をクリックします。  
  
6.  [スタートアップの種類] で [手動] または [自動] を選択している場合は、必要に応じて、 **[SQL Server Integration Services]** を右クリックし、 **[開始]、[停止]、または [再起動]** をクリックできます。  
  
7.  **[ファイル]** メニューの **[終了]** をクリックして **[サービス]** スナップインを終了します。  
  
## <a name="see-also"></a>参照  
 [Integration Services サービスを管理する](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  

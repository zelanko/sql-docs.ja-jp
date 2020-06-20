---
title: トランザクションを使用するようにパッケージを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], configuring packages to use
ms.assetid: 8bf14957-27b4-456b-81d9-e1a0e0ca94b7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9d16473832d321e252753fa79e8b3178f2c2dcf6
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921941"
---
# <a name="configure-a-package-to-use-transactions"></a>トランザクションを使用するようにパッケージを構成する
  トランザクションを使用するようにパッケージを構成する場合、次の 2 つのオプションがあります。  
  
-   パッケージで 1 つのトランザクションを使用する。 この場合、このトランザクションを *開始* するのはパッケージ自体で、パッケージ内の個々のタスクやコンテナーはこの 1 つのトランザクションに参加します。  
  
-   パッケージで複数のトランザクションを使用する。 この場合、パッケージでトランザクションがサポートされますが、トランザクションを実際に開始するのはパッケージ内のタスクやコンテナーになります。  
  
 次の手順では、これらの 2 つのオプションを構成する方法について説明します。  
  
## <a name="configuring-a-single-transaction"></a>1 つのトランザクションの構成  
 このオプションでは、パッケージ自体が 1 つのトランザクションを開始します。 パッケージの TransactionOption プロパティをに設定することによって、このトランザクションを開始するようにパッケージを構成し `Required` ます。  
  
 次に、この 1 つのトランザクションに特定のタスクやコンテナーを参加させます。 タスクまたはコンテナーをトランザクションに参加させるには、そのタスクまたはコンテナーの TransactionOption プロパティをに設定し `Supported` ます。  
  
#### <a name="to-configure-a-package-to-use-a-single-transaction"></a>1 つのトランザクションを使用するようにパッケージを構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、トランザクションを使用するように構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
5.  [**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Required` ます。  
  
6.  **[制御フロー]** タブのデザイン画面で、トランザクションに登録するタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。  
  
7.  [**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。  
  
    > [!NOTE]  
    >  トランザクションに接続を登録するには、トランザクションで接続を使用するタスクを登録します。 詳細については、「[Integration Services (SSIS) の接続](connection-manager/integration-services-ssis-connections.md)」を参照してください。  
  
8.  トランザクションに登録する各タスクおよびコンテナーに対して、手順 6. と 7. を繰り返します。  
  
## <a name="configuring-multiple-transactions"></a>複数のトランザクションの構成  
 このオプションでは、パッケージでトランザクションがサポートされますが、パッケージ自体はトランザクションを開始しません。 トランザクションをサポートするようにパッケージを構成するには、パッケージの TransactionOption プロパティをに設定し `Supported` ます。  
  
 次に、トランザクションを開始するかトランザクションに参加するように、パッケージ内の目的のタスクおよびコンテナーを構成します。 トランザクションを開始するようにタスクまたはコンテナーを構成するには、そのタスクまたはコンテナーの TransactionOption プロパティをに設定し `Required` ます。  
  
#### <a name="to-configure-a-package-to-use-multiple-transactions"></a>複数のトランザクションを使用するようにパッケージを構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、複数のトランザクションを使用するように構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックします。  
  
4.  制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
5.  [**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。  
  
    > [!NOTE]  
    >  パッケージでトランザクションがサポートされますが、トランザクションは、パッケージ内のタスクまたはコンテナーによって開始されます。  
  
6.  **[制御フロー]** タブのデザイン画面で、トランザクションを開始するパッケージ内のタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。  
  
7.  [**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Required` ます。  
  
8.  トランザクションがコンテナーによって開始される場合、トランザクションに登録するタスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。  
  
9. [**プロパティ**] ウィンドウで、transactionoption プロパティをに設定し `Supported` ます。  
  
    > [!NOTE]  
    >  トランザクションに接続を登録するには、トランザクションで接続を使用するタスクを登録します。 詳細については、「[Integration Services (SSIS) の接続](connection-manager/integration-services-ssis-connections.md)」を参照してください。  
  
10. トランザクションを開始する各タスクおよびコンテナーに対して、手順 6. ～ 9. を繰り返します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のトランザクション](integration-services-transactions.md)  
  
  

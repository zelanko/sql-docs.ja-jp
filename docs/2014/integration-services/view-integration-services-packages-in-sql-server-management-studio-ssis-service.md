---
title: SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 55ed3c5e5910438a601a649d80706967cf415e8e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972552"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a>SQL Server Management Studio で Integration Services パッケージを表示する (SSIS サービス)
    
> [!IMPORTANT]  
>  このトピックでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを管理するための Windows サービスである [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスについて説明します。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では、以前のリリースの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]との互換性を維持するために、このサービスをサポートしています。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降では、Integration Services サーバー上のパッケージなどのオブジェクトを管理できます。  
  
 この手順では、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に接続して、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが管理するパッケージの一覧を表示する方法について説明します。  
  
### <a name="to-connect-to-integration-services"></a>Integration Services に接続するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server Management Studio]** をクリックします。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスで、 **[サーバーの種類]** 一覧の **[Integration Services]** を選択し、 **[サーバー名]** ボックスにサーバー名を入力して **[接続]** をクリックします。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]に接続できない場合は、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが実行されていない可能性があります。 このサービスの状態を調べるには、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。 左ペインで、 **[SQL Server のサービス]** をクリックします。 右ペインで、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを見つけます。 サービスがまだ実行されていない場合は開始します。  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] が開きます。 既定では、Management Studio の左下隅にオブジェクト エクスプローラーが開きます。 オブジェクト エクスプローラーが開いていない場合は、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a>Integration Services サービスが管理するパッケージを表示するには  
  
1.  オブジェクト エクスプローラーで、[格納されたパッケージ] フォルダーを展開します。  
  
2.  [格納されたパッケージ] サブフォルダーを展開して、パッケージを表示します。  
  
## <a name="see-also"></a>参照  
 [SSIS サービス&#41;の Package Management &#40;](service/package-management-ssis-service.md)   
 [SQL Server Management Studio の使用 [SQL Server]](../database-engine/use-sql-server-management-studio.md)  
  
  

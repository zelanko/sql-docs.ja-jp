---
title: SQL Server Data Tools | でパッケージを実行します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ae5924e5fc1cad91b5e1511c61556ece70138dcb
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964549"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>SQL Server Data Tools でのパッケージの実行
  一般に、パッケージの開発、デバッグ、およびテストの段階では、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーからパッケージを実行すると、パッケージは常に即座に実行されます。  
  
 パッケージの実行中は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーによって [**進行状況**] タブにパッケージの実行の進行状況が表示されます。パッケージとそのタスクおよびコンテナーの開始時刻と終了時刻、および失敗したパッケージ内のすべてのタスクまたはコンテナーに関する情報を表示できます。 パッケージの実行が完了すると、[実行**結果**] タブに実行時情報が表示されたままになります。詳細については、「[制御フローのデバッグ](control-flow/control-flow.md)」の「進行状況レポート」を参照してください。  
  
 **デザイン時配置**。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージを実行すると、そのパッケージが構築されフォルダーに配置されます。 パッケージを実行する前に、パッケージを配置するフォルダーを指定できます。 フォルダーを指定しない場合、既定で **bin** フォルダーが使用されます。 こうした配置方法は、デザイン時配置と呼ばれます。  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>SQL Server Data Tools でパッケージを実行するには  
  
1.  ソリューションに複数のプロジェクトが含まれている場合は、ソリューション エクスプローラーで、パッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを右クリックし、 **[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ プロジェクトを設定します。  
  
2.  プロジェクトに複数のパッケージが含まれている場合は、ソリューション エクスプローラーで、パッケージの 1 つを右クリックし、 **[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ パッケージを設定します。  
  
3.  パッケージを実行するには、次のいずれかの手順を実行します。  
  
    -   実行するパッケージを開き、メニュー バーの **[デバッグ開始]** をクリックするか、F5 キーを押します。 パッケージの実行が完了したら、Shift キーを押しながら F5 キーを押して、デザイン モードに戻ります。  
  
    -   ソリューション エクスプローラーでパッケージを右クリックし、 **[パッケージの実行]** をクリックします。  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>デザイン時配置用に別のフォルダーを指定するには  
  
1.  ソリューション エクスプローラーで、実行するパッケージが含まれる [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト フォルダーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  [ ** \<project name> プロパティページ**] ダイアログボックスで、[**ビルド**] をクリックします。  
  
3.  OutputPath プロパティの値を更新して、デザイン時配置用に使用するフォルダーを指定し、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md)   
 [Integration Services &#40;SSIS&#41; パッケージ](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  

---
title: SQL Server Data Tools でパッケージを実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 23fd9f18468fa084ed526ab93f993a545749b2e1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174196"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>SQL Server Data Tools でのパッケージの実行
  一般に、パッケージの開発、デバッグ、およびテストの段階では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーからパッケージを実行すると、パッケージは常に即座に実行されます。  
  
 パッケージの実行中は、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[進行状況]** タブにパッケージの実行の進行状況が表示されます。パッケージおよびそのタスクおよびコンテナーの開始時間と終了時間に加え、パッケージ内で失敗したタスクまたはコンテナーに関する情報が表示されます。 パッケージの実行が完了した後は、 **[実行結果]** タブで実行時情報を確認できます。詳細については、[「制御フローのデバッグ」](control-flow/control-flow.md) の「進行状況レポート」を参照してください。  
  
 **デザイン時配置**。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] でパッケージを実行すると、そのパッケージが構築されフォルダーに配置されます。 パッケージを実行する前に、パッケージを配置するフォルダーを指定できます。 フォルダーを指定しない場合、既定で **bin** フォルダーが使用されます。 こうした配置方法は、デザイン時配置と呼ばれます。  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>SQL Server Data Tools でパッケージを実行するには  
  
1.  ソリューションに複数のプロジェクトが含まれている場合は、ソリューション エクスプローラーで、パッケージを含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを右クリックし、**[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ プロジェクトを設定します。  
  
2.  プロジェクトに複数のパッケージが含まれている場合は、ソリューション エクスプローラーで、パッケージの 1 つを右クリックし、 **[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ パッケージを設定します。  
  
3.  パッケージを実行するには、次のいずれかの手順を実行します。  
  
    -   実行するパッケージを開き、メニュー バーの **[デバッグ開始]** をクリックするか、F5 キーを押します。 パッケージの実行が完了したら、Shift キーを押しながら F5 キーを押して、デザイン モードに戻ります。  
  
    -   ソリューション エクスプローラーでパッケージを右クリックし、 **[パッケージの実行]** をクリックします。  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>デザイン時配置用に別のフォルダーを指定するには  
  
1.  ソリューション エクスプローラーで、実行するパッケージが含まれる [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト フォルダーを右クリックし、**[プロパティ]** をクリックします。  
  
2.  [**\<プロジェクト名> プロパティ ページ**] ダイアログ ボックスで、**[ビルド]** をクリックします。  
  
3.  OutputPath プロパティの値を更新して、デザイン時配置用に使用するフォルダーを指定し、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [プロジェクトとパッケージの実行](packages/run-integration-services-ssis-packages.md)   
 [Integration Services &#40;SSIS&#41; パッケージ](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
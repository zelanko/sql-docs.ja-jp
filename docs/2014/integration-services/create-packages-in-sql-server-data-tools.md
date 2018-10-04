---
title: SQL Server データ ツールでのパッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 24f73925210f51cfa942bc6b8228b5371aea33aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192892"
---
# <a name="create-packages-in-sql-server-data-tools"></a>SQL Server データ ツールでのパッケージの作成
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] デザイナーを使用して [!INCLUDE[ssIS](../includes/ssis-md.md)] で作成したパッケージは、ファイル システムに保存されます。 パッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] またはパッケージ ストアに保存するには、パッケージのコピーを保存する必要があります。 詳細については、「 [パッケージのコピーを保存する](../../2014/integration-services/save-a-copy-of-a-package.md)」を参照してください。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で新しいパッケージを作成するには、次のいずれかの方法を使用します。  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に含まれるパッケージ テンプレートを使用する。  
  
-   カスタム テンプレートを使用する。  
  
     新しいパッケージを作成するためのテンプレートとしてカスタム パッケージを使用する操作は簡単で、カスタム パッケージを DataTransformationItems フォルダーにコピーするだけです。 既定では、このフォルダーは、C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject にあります。  
  
-   既存のパッケージをコピーする。  
  
     再利用できる機能が既存のパッケージにある場合、既存のパッケージのオブジェクトをコピーして貼り付けることにより、新しいパッケージの制御フローとデータ フローをより短時間で構築できます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトでコピーと貼り付けを使用する方法の詳細については、「 [パッケージ オブジェクトの再利用](reuse-of-package-objects.md)」を参照してください。  
  
     新しいパッケージを作成する場合に、既存のパッケージをコピーするか、カスタム パッケージをテンプレートとして使用すると、既存のパッケージの名前と GUID もコピーされます。 新しいパッケージの名前と GUID は、コピー元のパッケージと区別できるように更新する必要があります。 たとえば、複数のパッケージに同じ GUID が使用されると、ログ データが所属するパッケージを特定することが難しくなります。 内の GUID を再生成することができます、`ID`プロパティの値を更新し、`Name`プロパティ [プロパティ] ウィンドウを使用して[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]します。 詳細については、「 [パッケージのプロパティを設定する](set-package-properties.md) 」と「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。  
  
-   テンプレートとして指定したカスタム パッケージを使用する。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行します。  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、簡単なインポートまたはエクスポートに使用できる完成したパッケージを作成します。 このウィザードでは、インポートまたはエクスポートをすぐに実行できるように、接続、変換元、および変換先が構成され、必要なすべてのデータ変換が追加されます。 パッケージを後で再び実行したり [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージを改良、強化するために、パッケージを保存することもできます。 ただし、パッケージを保存する場合は、パッケージを変更したり、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを実行したりする前に、既存の [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]プロジェクトにパッケージを追加しておく必要があります。  
  
 次の手順が作成またはでパッケージを削除する方法について説明する[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]します。  
  
 既定のパッケージ テンプレートを使用して基本的なパッケージを作成する方法のデモ ビデオについては、「 [基本パッケージの作成 (SQL Server ビデオ)](http://go.microsoft.com/fwlink/?LinkId=131023)」を参照してください。  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>パッケージ テンプレートを使用して SQL Server データ ツールでパッケージを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、 **[SSIS パッケージ]** フォルダーを右クリックし、 **[新しい SSIS パッケージ]** をクリックします。  
  
3.  必要に応じて、制御フロー、データ フロー タスク、およびイベント ハンドラーをパッケージに追加します。 詳細については、「[制御フロー](control-flow/control-flow.md)」、「[データ フロー](data-flow/data-flow.md)」、および「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](integration-services-ssis-event-handlers.md)」を参照してください。  
  
4.  **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。  
  
    > [!NOTE]  
    >  空のパッケージも保存できます。  
  
  

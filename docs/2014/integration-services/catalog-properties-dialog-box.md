---
title: '[カタログのプロパティ] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f1a4a9d7a74e47d609c319f90b07d8ebfdce00e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439139"
---
# <a name="catalog-properties-dialog-box"></a>[カタログのプロパティ] ダイアログ ボックス
  [カタログのプロパティ] ダイアログ ボックスを使用すると、SSISDB カタログを構成できます。 カタログプロパティは、機微なデータを暗号化する方法、操作およびプロジェクトのバージョン管理データを保持する方法、および検証操作がタイムアウトするタイミングを定義します。SSISDB カタログは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクト、パッケージ、パラメーター、および環境のための中央のストレージと管理ポイントです。  
  
 また、カタログ プロパティを catalog.catalog_property ビューで表示し、catalog.configure_catalog ストアド プロシージャを使用してこれらのプロパティを設定できます。 詳細については、「[catalog.catalog_properties (SSISDB データベース)](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database)」および「[catalog.configure_catalog (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database)」を参照してください。  
  
 SSISDB カタログを作成する方法の詳細については、「 [SSIS カタログの作成](catalog/ssis-catalog.md)」を参照してください。  
  
 **どうしたいんですか。**  
  
-   [[カタログのプロパティ] ダイアログ ボックスを開く](#open_dialog)  
  
-   [オプションの構成](#options)  
  
##  <a name="open-the-catalog-properties-dialog-box"></a><a name="open_dialog"></a>[カタログのプロパティ] ダイアログボックスを開く  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]を開きます。  
  
2.  Microsoft SQL Server データベース エンジンに接続します。  
  
3.  オブジェクト エクスプローラーで、 **[Integration Services]** ノードを展開します。 **[SSISDB]** を右クリックし、 **[プロパティ]** をクリックします。  
  
##  <a name="configure-the-options"></a><a name="options"></a>オプションを構成する  
  
### <a name="options"></a>オプション  
 次の表では、ダイアログ ボックスに示される特定のプロパティと、catalog.catalog_property ビュー内の対応するプロパティについて説明します。  
  
|プロパティ名 ([カタログのプロパティ] ダイアログ ボックス)|プロパティ名 (catalog.catalog_property ビュー)|説明|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|暗号化アルゴリズムの名前|ENCRYPTION_CLEANUP_ENABLED|カタログ内の機密性の高いパラメーター値を暗号化するために使用される暗号化の種類を指定します。 使用できる値を次に示します。<br /><br /> **DES**<br /><br /> **TRIPLE_DES**<br /><br /> **TRIPLE_DES_3KEY**<br /><br /> **DESPX**<br /><br /> **AES_128**<br /><br /> **AES_192**<br /><br /> **AES_256** (既定値)|  
|検証のタイムアウト (秒)|VALIDATION_TIMEOUT|プロジェクトの検証またはパッケージの検証を停止するまで実行できる最大秒数を指定します。 既定値は 300 秒です。<br /><br /> 検証の実行は、非同期操作です。 プロジェクトまたはパッケージのサイズが大きくなるほど、検証に要する時間も長くなります。<br /><br /> プロジェクトとパッケージの検証方法の詳細については、「 [式における Integration Services データ型](expressions/integration-services-data-types-in-expressions.md)」を参照してください。|  
|ログを定期的に消去する|OPERATION_CLEANUP_ENABLED|操作のクリーンアップ SQL Server エージェント ジョブを実行することを示すには、このプロパティを True に設定します。 それ以外の場合は、このプロパティを False に設定します。|  
|保有期間 (日)|RETENTION_WINDOW|操作データの最大保有期間を日数で指定します。 指定された日数を経過したデータは、操作のクリーンアップ SQL エージェント ジョブによって削除されます。|  
|プロジェクトごとのバージョンの最大数|MAX_PROJECT_VERSIONS|カタログに格納されるプロジェクトのバージョンの数を指定します。 最大数を超えるプロジェクトのバージョンは、プロジェクト バージョンのクリーンアップ ジョブを実行したときに削除されます。|  
  
  

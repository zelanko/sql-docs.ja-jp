---
title: "ストアド プロシージャ (Integration Services カタログ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- stored procedures [Integration Services]
ms.assetid: a6ccd884-108f-4fb6-95ad-00b9cb65d5d6
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 21715bf65f3a85669dfe823511ddb9b6c2dd4d57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="stored-procedures-integration-services-catalog"></a>ストアド プロシージャ (Integration Services カタログ)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションの内容について説明します、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを管理するために使用できる[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のインスタンスに配置されているプロジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 呼び出す、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ストアド プロシージャを追加、削除、変更、またはオブジェクトに格納されているを実行する、 **SSISDB**カタログ。  
  
 カタログの既定の名前は、SSISDB です。 カタログに格納されているオブジェクトには、プロジェクト、パッケージ、パラメーター、環境、および操作履歴があります。  
  
 データベース ビューとストアド プロシージャを直接使用することも、マネージ API を呼び出すカスタム コードを記述することもできます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]マネージ API は、ビューに対してクエリし、多くのタスクを実行するには、このセクションで説明されているストアド プロシージャを呼び出します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
 パッケージ データ フロー内のコンポーネントの出力で、データ タップを追加します。  
  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
 パッケージ データ フロー内の特定のデータ フロー パスにデータ タップを追加します。  
  
 [catalog.check_schema_version](../../integration-services/system-stored-procedures/catalog-check-schema-version.md)  
 SSISDB カタログ スキーマであるかどうかを決定し、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]バイナリ (ISServerExec および SQLCLR アセンブリ) に互換性ができます。  
  
 [catalog.clear_object_parameter_value & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md)  
 既存のパラメーターの値をクリア[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]プロジェクトまたはパッケージをサーバーに格納されています。  
  
 [catalog.configure_catalog & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md)  
 カタログ プロパティを特定の値に設定することによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログを構成します。  
  
 [catalog.create_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
 環境を作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.create_environment_reference &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
 環境参照をプロジェクトの作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.create_environment_variable &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
 環境変数を作成、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.create_execution & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行のインスタンスを作成します。  
  
 [catalog.create_execution_dump](../../integration-services/system-stored-procedures/catalog-create-execution-dump.md)  
 実行中のパッケージを一時停止させ、ダンプ ファイルを作成します。  
  
 [catalog.create_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーを作成します。  
  
 [catalog.delete_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーから環境を削除します。  
  
 [catalog.delete_environment_reference &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
 環境参照をプロジェクトから削除、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.delete_environment_variable &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの環境から環境変数を削除します。  
  
 [catalog.delete_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
 フォルダーを削除、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.delete_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
 内のフォルダーから既存のプロジェクトを削除、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.deny_permission & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのセキュリティ保護可能なオブジェクトに対する権限を拒否します。  
  
 [catalog.deploy_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーにプロジェクトを配置するか、以前に配置した既存のプロジェクトを更新します。  
  
 [catalog.get_parameter_values & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md)  
 解決し、プロジェクトおよび対応するパッケージから既定のパラメーター値の取得、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.get_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの既存のプロジェクトのプロパティを取得します。  
  
 [catalog.grant_permission & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
 セキュリティ保護可能なオブジェクトに対する権限を許可、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.move_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
 環境を内の別の 1 つのフォルダーに移動、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.move_project &#40;&#40;SSISDB データベース&#41;](../Topic/catalog.move_project%20\(\(SSISDB%20Database\).md)  
 プロジェクトを内の別の 1 つのフォルダーに移動、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.remove_data_tap](../../integration-services/system-stored-procedures/catalog-remove-data-tap.md)  
 実行内のコンポーネント出力からデータ タップを削除します。  
  
 [catalog.rename_environment &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの環境の名前を変更します。  
  
 [catalog.rename_folder &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
 内のフォルダーの名前を変更、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.restore_project &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
 プロジェクトの復元、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]以前のバージョンのカタログ。  
  
 [catalog.revoke_permission & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md)  
 セキュリティ保護可能なオブジェクトに対する権限を取り消します、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_environment_property &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
 環境のプロパティを設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_environment_reference_type &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
 プロジェクトの既存の環境参照に関連付けられている参照の種類と環境名の設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_environment_variable_property &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
 環境変数のプロパティを設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_environment_variable_protection & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md)  
 環境変数のセンシティビティ ビットを設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_environment_variable_value &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの環境変数の値を設定します。  
  
 [catalog.set_execution_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 実行のインスタンスにパラメーターの値を設定、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.set_execution_property_override_value](../../integration-services/system-stored-procedures/catalog-set-execution-property-override-value.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行のインスタンスにプロパティの値を設定します。  
  
 [catalog.set_folder_description &#40;SSISDB データベース&#41;](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのフォルダーの説明を設定します。  
  
 [catalog.set_object_parameter_value & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパラメーターの値を設定します。 他の値が割り当てられていない場合は、値を環境変数に関連付けるか、または既定で使用されるリテラル値を割り当てます。  
  
 [catalog.start_execution & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログの実行のインスタンスを起動します。  
  
 [catalog.startup](../../integration-services/system-stored-procedures/catalog-startup.md)  
 SSISDB カタログに対する操作の状態のメンテナンスを実行します。  
  
 [catalog.stop_operation & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md)  
 検証または実行のインスタンスを停止、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
 [catalog.validate_package & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md)  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパッケージを非同期的に検証します。  
  
 [catalog.validate_project & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md)  
 プロジェクトを非同期的に検証、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
[catalog.add_execution_worker & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)   
追加、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト ワーカーにスケール アウトでの実行のインスタンス。

[catalog.enable_worker_agent & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md)   
スケール アウト マスターでこの操作のスケール アウト ワーカーを有効にする[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。

[catalog.disable_worker_agent & #40 です。SSISDB データベース &#41;](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)   
スケール アウト マスターでこの操作のスケール アウト ワーカーを無効にする[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。




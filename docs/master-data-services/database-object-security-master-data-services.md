---
description: データベース オブジェクト セキュリティ (マスター データ サービス)
title: データベース オブジェクト セキュリティ
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f9b2089b72f11872df0dc0c0b2758fb8272a4c06
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88344908"
---
# <a name="database-object-security-master-data-services"></a>データベース オブジェクト セキュリティ (マスター データ サービス)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースでは、データは複数のデータベース テーブルに格納されており、ビューで表示できます。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで保護されている可能性がある情報は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースにアクセスできるユーザーであれば参照できます。  
  
 具体的には、従業員の給与情報が Employee モデルに含まれており、企業の財務情報が Account モデルに含まれている場合を考えることができます。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイスでこれらのモデルへのユーザー アクセスを拒否できますが、データベースへのアクセス権を持つユーザーはこのデータを表示できます。  
  
 ユーザーが固有のデータを使用できるように、データベース オブジェクトに権限を付与できます。 権限付与の詳細については、「[GRANT (オブジェクトの権限の許可) (Transact-SQL)](../t-sql/statements/grant-object-permissions-transact-sql.md)」を参照してください。 SQL server の保護の詳細については、「 [SQL Server の保護](../relational-databases/security/securing-sql-server.md)」を参照してください。  
  
 次のタスクでは [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースへのアクセスが必要です。  
  
-   [データのステージング](#Staging)  
  
-   [ビジネス ルールに対してデータを検証する](#rules)  
  
-   [バージョンを削除する](#Versions)  
  
-   [階層メンバーの権限を直ちに適用する](#Hierarchy)  
  
-   [システム設定を構成する](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> データをステージングする  
 次の表では、セキュリティ保護可能な各リソースの名前の一部に "name" を使用しています。 これは、エンティティの作成時に指定するステージング テーブルの名前を示します。 詳細については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
|アクション|[セキュリティ保護可能なリソース]|アクセス許可|  
|------------|----------------|-----------------|  
|リーフ メンバーとその属性を作成、更新、および削除します。|stg.name_Leaf|必須: INSERT<br /><br /> オプション: SELECT および UPDATE|  
|リーフ ステージング テーブルから MDS データベースの適切なテーブルにデータを読み込む|stg.udp_name_Leaf|EXECUTE|  
|統合メンバーとその属性を作成、更新、および削除します。|stg.name_Consolidated|必須: INSERT<br /><br /> オプション: SELECT および UPDATE|  
|統合ステージング テーブルから MDS データベースの適切なテーブルにデータを読み込む|stg.udp_name_Consolidated|EXECUTE|  
|明示的階層内でメンバーを移動する。|stg.name_Relationship|必須: INSERT<br /><br /> オプション: SELECT および UPDATE|  
|リレーションシップ ステージング テーブルから MDS の適切なテーブルにデータを読み込む|stg.udp_name_Relationship|EXECUTE|  
|ステージング テーブルのデータが MDS データベース テーブルに挿入されたときに発生したエラーを表示する|stg.udp_name_Relationship|SELECT|  
  
 詳細については、「 [概要: テーブルからのデータのインポート &#40;マスターデータサービス&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a> ビジネスルールに対してデータを検証する  
  
|アクション|セキュリティ保護可能|アクセス許可|  
|------------|---------------|-----------------|  
|ビジネス ルールに対してデータのバージョンを検証する|mdm.udpValidateModel|EXECUTE|  
  
 詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)」を参照してください。  
  
##  <a name="deleting-versions"></a><a name="Versions"></a> バージョンの削除  
  
|アクション|[セキュリティ保護可能なリソース]|アクセス許可|  
|------------|----------------|-----------------|  
|削除するバージョンの ID を決定する|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|モデルのバージョンを削除する|mdm.udpVersionDelete|EXECUTE|  
  
 詳細については、「[バージョンを削除する (マスター データ サービス)](../master-data-services/delete-a-version-master-data-services.md)」を参照してください。  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a> 階層メンバーの権限を直ちに適用する  
  
|アクション|[セキュリティ保護可能なリソース]|アクセス許可|  
|------------|----------------|-----------------|  
|メンバー権限を直ちに適用する|mdm.udpSecurityMemberProcessRebuildModel|EXECUTE|  
  
 詳細については、「[メンバー権限を直ちに適用する (マスター データ サービス)](../master-data-services/immediately-apply-member-permissions-master-data-services.md)」を参照してください。  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a> システム設定の構成  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]での動作を制御するために構成可能なシステム設定が用意されています。 これらの設定は [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整できます。または、UPDATE アクセス権を持つ場合は、mdm.tblSystemSetting データベース テーブルで直接調整できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ (マスター データ サービス)](../master-data-services/security-master-data-services.md)  
  
  

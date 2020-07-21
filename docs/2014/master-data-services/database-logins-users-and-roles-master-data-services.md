---
title: データベース ログイン、ユーザー、およびロール (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], database roles
- database [Master Data Services], users
- security [Master Data Services], database users
- database [Master Data Services], roles
- database [Master Data Services], logins
- security [Master Data Services], database logins
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 416ae500d940eb31eee3294edd07c289b124b6c4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971652"
---
# <a name="database-logins-users-and-roles-master-data-services"></a>データベース ログイン、ユーザー、およびロール (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] データベースをホストする [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに自動的にインストールされるログイン、ユーザー、およびロールがあります。 これらのログイン、ユーザー、およびロールは変更しないでください。  
  
## <a name="logins"></a>Login  
  
|ログイン|説明|  
|-----------|-----------------|  
|`mds_dlp_login`|UNSAFE アセンブリを作成できます。<br /><br /> - ランダムに生成されたパスワードでのログインは無効です。<br /><br /> - [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、dbo にマップされます。<br /><br /> - msdb の場合は、mds_clr_user がこのログインにマップされます。<br /><br /> <br /><br /> 詳細については、「 [アセンブリの作成](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」を参照してください。|  
|`mds_email_login`|通知に使用されるログインは有効です。<br /><br /> msdb および [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、mds_email_user がこのログインにマップされます。|  
  
## <a name="msdb-users"></a>msdb ユーザー  
  
|User|説明|  
|----------|-----------------|  
|`mds_clr_user`|使用されていません。<br /><br /> mds_dlp_login にマップされます。|  
|`mds_email_user`|通知に使用します。<br /><br /> mds_email_login にマップされます。<br /><br /> DatabaseMailUserRole ロールのメンバーです。|  
  
## <a name="master-data-services-database-users"></a>マスター データ サービス データベース ユーザー  
  
|User|説明|  
|----------|-----------------|  
|`mds_email_user`|通知に使用します。<br /><br /> mdm スキーマに対する SELECT 権限があります。<br /><br /> mdm.MemberGetCriteria ユーザー定義テーブル型に対する EXECUTE 権限があります。<br /><br /> mdm.udpNotificationQueueActivate ストアド プロシージャに対する EXECUTE 権限があります。|  
|**mds_schema_user**|mdm スキーマと mdq スキーマを所有します。 既定のスキーマは mdm です。<br /><br /> ログインはマップされません。|  
|**mds_ssb_user**|Service Broker タスクを実行するために使用します。<br /><br /> すべてのスキーマに対する DELETE、INSERT、REFERENCES、SELECT、および UPDATE 権限があります。<br /><br /> ログインはマップされません。|  
  
## <a name="master-data-services-database-role"></a>マスター データ サービス データベース ロール  
  
|Role|説明|  
|----------|-----------------|  
|`mds_exec`|このロールには、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] Web アプリケーションを作成してアプリケーション プールのアカウントを指定したときに [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] で指定したアカウントが含まれます。 mds_exec ロールには次の権限があります。<br /><br /> すべてのスキーマに対する**EXECUTE**権限。<br /><br /> これらのテーブルに対する**ALTER**、 **INSERT**、および**SELECT**権限:<br />mdm.tblStgMember<br />mdm.tblStgMemberAttribute<br />mdm.tbleStgRelationship<br /><br /> これらのテーブルに対する**SELECT**権限:<br />mdm.tblUser<br />mdm.tblUserGroup<br />mdm.tblUserPreference<br /><br /> 次のビューに対する**SELECT**権限:<br />mdm.viw_SYSTEM_SECURITY_NAVIGATION<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br />mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br />mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## <a name="schemas"></a>スキーマ  
  
|Role|説明|  
|----------|-----------------|  
|`mdm`|mdq スキーマに含まれている関数以外のすべての [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース オブジェクトおよび Service Broker オブジェクトが含まれます。|  
|`mdq`|正規表現または類似性に基づくメンバーの結果のフィルター処理や書式設定通知電子メールに関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース関数が含まれます。|  
|**stg**|ステージング処理に関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース テーブル、ストアド プロシージャ、およびビューが含まれます。 これらのオブジェクトは削除しないでください。 ステージング処理の詳細については、「[データのインポート &#40;マスターデータサービス&#41;](overview-importing-data-from-tables-master-data-services.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [データベース オブジェクト セキュリティ &#40;マスター データ サービス&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  

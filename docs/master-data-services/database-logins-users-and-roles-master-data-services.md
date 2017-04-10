---
title: "データベース ログイン、ユーザー、およびロール (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [マスター データ サービス], データベース ロール"
  - "データベース [マスター データ サービス], ユーザー"
  - "セキュリティ [マスター データ サービス], データベース ユーザー"
  - "データベース [マスター データ サービス], ロール"
  - "データベース [マスター データ サービス], ログイン"
  - "セキュリティ [マスター データ サービス], データベース ログイン"
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# データベース ログイン、ユーザー、およびロール (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースをホストする [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] インスタンスに自動的にインストールされるログイン、ユーザー、およびロールがあります。 これらのログイン、ユーザー、およびロールは変更しないでください。  
  
## ログイン  
  
|Login|Description|  
|-----------|-----------------|  
|**mds_dlp_login**|UNSAFE アセンブリを作成できます。 詳細については、「[アセンブリの作成](../relational-databases/clr-integration/assemblies/creating-an-assembly.md)」を参照してください。<br /><br /> - ランダムに生成されたパスワードでのログインは無効です。<br /><br /> - [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、dbo にマップされます。<br /><br /> - msdb の場合は、mds_clr_user がこのログインにマップされます。|  
|**mds_email_login**|通知に使用されるログインは有効です。<br /><br /> msdb および [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの場合は、mds_email_user がこのログインにマップされます。|  
  
## msdb ユーザー  
  
|ユーザー|Description|  
|----------|-----------------|  
|**mds_clr_user**|使用されていません。 mds_dlp_login にマップされます。|  
|**mds_email_user**|通知に使用します。<br /><br /> - mds_email_login にマップされます。<br /><br /> - DatabaseMailUserRole ロールのメンバーです。|  
  
## マスター データ サービス データベース ユーザー  
  
|ユーザー|Description|  
|----------|-----------------|  
|**mds_email_user**|通知に使用します。<br /><br /> - mdm スキーマに対する SELECT 権限があります。<br /><br /> - mdm.MemberGetCriteria ユーザー定義テーブル型に対する EXECUTE 権限があります。<br /><br /> - mdm.udpNotificationQueueActivate ストアド プロシージャに対する EXECUTE 権限があります。|  
|**mds_schema_user**|mdm スキーマと mdq スキーマを所有します。 既定のスキーマは mdm です。<br /><br /> ログインはマップされません。|  
|**mds_ssb_user**|Service Broker タスクを実行するために使用します。<br /><br /> - すべてのスキーマに対する DELETE、INSERT、REFERENCES、SELECT、および UPDATE 権限があります。<br /><br /> - ログインはマップされません。|  
  
## マスター データ サービス データベース ロール  
  
|ロール|Description|Permissions|  
|----------|-----------------|-----------------|  
|**mds_exec**|このロールには、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]Web アプリケーションを作成してアプリケーション プールのアカウントを指定したときに[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]で指定したアカウントが含まれます。|すべてのスキーマに対する EXECUTE 権限<br /><br /> <br /><br /> 次のテーブルに対する ALTER、INSERT、および SELECT 権限<br /><br /> mdm.tblStgMember<br /><br /> mdm.tblStgMemberAttribute<br /><br /> mdm.tbleStgRelationship<br /><br /> <br /><br /> 次のテーブルに対する SELECT 権限<br /><br /> mdm.tblUser<br /><br /> mdm.tblUserGroup<br /><br /> mdm.tblUserPreference<br /><br /> <br /><br /> 次のビューに対する SELECT 権限<br /><br /> mdm.viw_SYSTEM_SECURITY_NAVIGATION<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br /><br /> mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## スキーマ  
  
|ロール|Description|  
|----------|-----------------|  
|**mdm**|mdq スキーマに含まれている関数以外のすべての [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース オブジェクトおよび Service Broker オブジェクトが含まれます。|  
|**mdq**|正規表現または類似性に基づくメンバーの結果のフィルター処理や書式設定通知電子メールに関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース関数が含まれます。|  
|**stg**|ステージング処理に関連する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース テーブル、ストアド プロシージャ、およびビューが含まれます。 これらのオブジェクトは削除しないでください。 ステージング処理の詳細については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。|  
  
## 参照  
 [データベース オブジェクト セキュリティ (マスター データ サービス)](../master-data-services/database-object-security-master-data-services.md)  
  
  
---
title: "Integration Services のロール (SSIS サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [Integration Services], ロール"
  - "db_ssisoperator ロール"
  - "db_ssisadmin ロール"
  - "固定データベース ロール [Integration Services]"
  - "パッケージ [Integration Services], セキュリティ"
  - "ロール [Integration Services]"
  - "db_ssisltduser ロール"
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Integration Services のロール (SSIS サービス)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されたパッケージに安全にアクセスするための固定データベース レベルの特定のロールを提供します。 利用可能なロールは、パッケージを SSIS カタログ データベース (SSISDB) に保存するか、msdb データベースに保存するかどうかによって異なります。  
  
## SSIS カタログ データベース (SSISDB) のロール  
 SSIS カタログ データベース (SSISDB) は、パッケージやパッケージに関する情報に安全にアクセスするための、次の固定データベース レベルのロールを提供します。  
  
-   **ssis_admin**。 このロールは、SSIS カタログ データベースに対する完全な管理アクセスを提供します。  
  
-   **ssis_logreader**。このロールは、ビュー関連のすべての SSISDB 運用ログにアクセスする権限を提供します。  
  
     ビューの一覧には、[catalog].[projects]、[catalog].[packages]、[catalog].[operations]、[catalog].[extended_operation_info]、[catalog].[operation_messages]、[catalog].[event_messages]、[catalog].[execution_data_statistics]、[catalog].[execution_component_phases]、[catalog].[execution_data_taps]、[catalog].[event_message_context]、[catalog].[executions]、[catalog].[executables]、[catalog].[executable_statistics]、[catalog].[validations]、[catalog].[execution_parameter_values] [catalog].[execution_property_override_values] が含まれます。  
  
## msdb データベースのロール  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] には、**msdb** に保存されたパッケージへのアクセスを制御するために、**db_ssisadmin**、**db_ssisltduser**、**db_ssisoperator** というデータベース レベルの 3 つの固定ロールがあります。 パッケージにロールを割り当てるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。 ロールの割り当ては、 **msdb** データベースに保存されます。  
  
### 読み取りアクションと書き込みアクション  
 次の表で、Windows の読み取りおよび書き込みアクションと、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] での固定データベース レベル ロールの読み取りおよび書き込みアクションについて説明します。  
  
|ロール|読み取りアクション|書き込みアクション|  
|----------|-----------------|------------------|  
|**db_ssisadmin**<br /><br /> または<br /><br /> **sysadmin**|独自のパッケージを列挙する。<br /><br /> すべてのパッケージを列挙する。<br /><br /> 独自のパッケージを表示する。<br /><br /> すべてのパッケージを表示する。<br /><br /> 独自のパッケージを実行する。<br /><br /> すべてのパッケージを実行する。<br /><br /> 独自のパッケージをエクスポートする。<br /><br /> すべてのパッケージをエクスポートする。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント内のすべてのパッケージを実行する。|パッケージをインポートする。<br /><br /> 独自のパッケージを削除する。<br /><br /> すべてのパッケージを削除する。<br /><br /> 独自のパッケージのロールを変更する。<br /><br /> すべてのパッケージのロールを変更する。<br /><br /> <br /><br /> **\*\*警告\*\*** db_ssisadmin ロールおよび dc_admin ロールのメンバーは、特権を sysadmin に昇格できる可能性があります。 このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エージェントの sysadmin セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを実行できるためです。 メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、db_ssisadmin ロールおよび dc_admin ロールには sysadmin メンバーのみを追加するようにします。|  
|**db_ssisltduser**|独自のパッケージを列挙する。<br /><br /> すべてのパッケージを列挙する。<br /><br /> 独自のパッケージを表示する。<br /><br /> 独自のパッケージを実行する。<br /><br /> 独自のパッケージをエクスポートする。|パッケージをインポートする。<br /><br /> 独自のパッケージを削除する。<br /><br /> 独自のパッケージのロールを変更する。|  
|**db_ssisoperator**|すべてのパッケージを列挙する。<br /><br /> すべてのパッケージを表示する。<br /><br /> すべてのパッケージを実行する。<br /><br /> すべてのパッケージをエクスポートする。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント内のすべてのパッケージを実行する。|なし|  
|**Windows 管理者**|実行中のすべてのパッケージの実行時の詳細を表示する。|現在実行中のパッケージをすべて停止する。|  
  
### sysssispackages テーブル  
 **msdb** の **sysssispackages** テーブルには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に保存されるパッケージが格納されています。 詳細については、「[sysssispackages &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysssispackages-transact-sql.md)」を参照してください。  
  
 **sysssispackages** テーブルには、パッケージに割り当てられるロールに関する情報が含まれている列があります。  
  
-   **readerrole** 列は、パッケージへの読み取りアクセスが可能なロールを指定します。  
  
-   **writerrole** 列は、パッケージへの書き込みアクセスが可能なロールを指定します。  
  
-   **ownersid** 列には、パッケージを作成したユーザーの一意なセキュリティ識別子が格納されています。 この列により、パッケージの所有者が定義されます。  
  
### Permissions  
 既定では、**db_ssisadmin** および **db_ssisoperator** の各固定データベース レベル ロールの権限、およびパッケージを作成したユーザーの一意なセキュリティ識別子は、パッケージのリーダー ロールに適用されます。**db_ssisadmin** ロールの権限およびパッケージを作成したユーザーの一意なセキュリティ識別子は、ライター ロールに適用されます。 ユーザーは、パッケージの読み取りアクセスを行うには **db_ssisadmin**、**db_ssisltduser**、または **db_ssisoperator** ロールのメンバーである必要があります。 書き込みアクセスを行うには **db_ssisadmin** ロールのメンバーである必要があります。  
  
### パッケージへのアクセス  
 固定データベース レベル ロールは、ユーザー定義ロールと組み合わせて使用されます。 ユーザー定義ロールとは、ユーザーが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で作成するロールのことで、権限をパッケージに割り当てるために使用します。 パッケージにアクセスするには、ユーザーは、ユーザー定義ロールおよび関連する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 固定データベースレベル ロールのメンバーである必要があります。 たとえば、ユーザーがパッケージに割り当てられている **AuditUsers** ユーザー定義ロールのメンバーである場合、パッケージに対する読み取りアクセスを得るには、さらに **db_ssisadmin**、**db_ssisltduser**、または **db_ssisoperator** ロールのメンバーでもある必要があります。  
  
 ユーザー定義ロールをパッケージに割り当てていない場合、パッケージへのアクセスは固定データベース レベル ロールによって決定されます。  
  
 ユーザー定義ロールを使用するには、パッケージに割り当てる前に、あらかじめ **msdb** データベースに追加しておく必要があります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、新しいデータベース ロールを作成できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データベース レベルのロールは、msdb データベース内の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] システム テーブルに対する権限を付与します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER サービス) は、データベース エンジンに接続して **msdb** データベースにアクセスするためにあらかじめ起動されている必要があります。  
  
 パッケージにロールを割り当てるには、次のタスクを完了する必要があります。  
  
-   **オブジェクト エクスプローラーを開いて Integration Services に接続する**  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してパッケージにロールを割り当てるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーを開き、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に接続する必要があります。  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを起動してから、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に接続します。  
  
-   **リーダー ロールおよびライター ロールをパッケージに割り当てる**  
  
     リーダー ロールおよびライター ロールをそれぞれのパッケージに割り当てることができます。  
  
## 関連タスク  
  
-   [リーダー ロールおよびライター ロールをパッケージに割り当てる](../../integration-services/service/assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [ユーザー定義ロールを作成する](../../integration-services/service/create-a-user-defined-role.md)  
  
-   [Integration Services に接続する](../../integration-services/service/connect-to-integration-services.md)  
  
  
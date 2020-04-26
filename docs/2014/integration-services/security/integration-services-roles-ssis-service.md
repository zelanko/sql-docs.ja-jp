---
title: Integration Services のロール (SSIS サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 43c1c932565ae3df666be10a1b89794ecd720135
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/25/2020
ms.locfileid: "62766674"
---
# <a name="integration-services-roles-ssis-service"></a>Integration Services のロール (SSIS サービス)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]には、パッケージへのアクセスを制御`db_ssisadmin`するための3つの固定データベースレベルロール、、 **db_ssisltduser**、および**db_ssisoperator**が含まれています。 ロールは、 `msdb`の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに保存されているパッケージにのみ実装できます。 パッケージにロールを割り当てるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。 ロールの割り当ては`msdb`データベースに保存されます。  
  
## <a name="read-and-write-actions"></a>読み取りアクションと書き込みアクション  
 次の表で、Windows の読み取りおよび書き込みアクションと、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]での固定データベース レベル ロールの読み取りおよび書き込みアクションについて説明します。  
  
|Role|読み取りアクション|書き込みアクション|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> または<br /><br /> `sysadmin`|独自のパッケージを列挙する。<br /><br /> すべてのパッケージを列挙する。<br /><br /> 独自のパッケージを表示する。<br /><br /> すべてのパッケージを表示する。<br /><br /> 独自のパッケージを実行する。<br /><br /> すべてのパッケージを実行する。<br /><br /> 独自のパッケージをエクスポートする。<br /><br /> すべてのパッケージをエクスポートする。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント内のすべてのパッケージを実行する。|パッケージをインポートする。<br /><br /> 独自のパッケージを削除する。<br /><br /> すべてのパッケージを削除する。<br /><br /> 独自のパッケージのロールを変更する。<br /><br /> すべてのパッケージのロールを変更する。<br /><br /> <br /><br /> ** \*重要\* \* **Db_ssisadmin ロールおよび dc_admin ロールのメンバーは、特権を sysadmin に昇格させることができます。 このような特権の昇格が発生するのは、それらのロールが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを変更でき、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エージェントの sysadmin セキュリティ コンテキストを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを実行できるためです。 メンテナンス プラン、データ コレクション セット、およびその他の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行時にこの特権の昇格を防ぐには、特権が制限されたプロキシ アカウントを使用するようにパッケージを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを構成するか、db_ssisadmin ロールおよび dc_admin ロールには sysadmin メンバーのみを追加するようにします。|  
|**db_ssisltduser**|独自のパッケージを列挙する。<br /><br /> すべてのパッケージを列挙する。<br /><br /> 独自のパッケージを表示する。<br /><br /> 独自のパッケージを実行する。<br /><br /> 独自のパッケージをエクスポートする。|パッケージをインポートする。<br /><br /> 独自のパッケージを削除する。<br /><br /> 独自のパッケージのロールを変更する。|  
|**db_ssisoperator**|すべてのパッケージを列挙する。<br /><br /> すべてのパッケージを表示する。<br /><br /> すべてのパッケージを実行する。<br /><br /> すべてのパッケージをエクスポートする。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント内のすべてのパッケージを実行する。|None|  
|**Windows 管理者**|実行中のすべてのパッケージの実行時の詳細を表示する。|現在実行中のパッケージをすべて停止する。|  
  
## <a name="sysssispackages-table"></a>sysssispackages テーブル  
 `msdb`の**sysssispackages**テーブルには、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]保存されているパッケージが含まれています。 詳細については、「[sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql)」を参照してください。  
  
 **sysssispackages** テーブルには、パッケージに割り当てられるロールに関する情報が含まれている列があります。  
  
-   **readerrole** 列は、パッケージへの読み取りアクセスが可能なロールを指定します。  
  
-   **writerrole** 列は、パッケージへの書き込みアクセスが可能なロールを指定します。  
  
-   **ownersid** 列には、パッケージを作成したユーザーの一意なセキュリティ識別子が格納されています。 この列により、パッケージの所有者が定義されます。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 `db_ssisadmin`および**db_ssisoperator**固定データベースレベルロールの権限と、パッケージを作成したユーザーの一意のセキュリティ識別子がパッケージの閲覧者ロールに適用されます。また、 `db_ssisadmin`ロールの権限と、パッケージを作成したユーザーの一意のセキュリティ識別子が、ライターロールに適用されます。 パッケージに対する読み取りアクセス権を持つ`db_ssisadmin`ユーザーは、、 **db_ssisltduser**、または**db_ssisoperator**ロールのメンバーである必要があります。 書き込みアクセス権を持つユーザーは、 `db_ssisadmin`ロールのメンバーである必要があります。  
  
## <a name="access-to-packages"></a>パッケージへのアクセス  
 固定データベース レベル ロールは、ユーザー定義ロールと組み合わせて使用されます。 ユーザー定義ロールとは、ユーザーが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で作成するロールのことで、権限をパッケージに割り当てるために使用します。 パッケージにアクセスするには、ユーザーは、ユーザー定義ロールおよび関連する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 固定データベースレベル ロールのメンバーである必要があります。 たとえば、ユーザーがパッケージに割り当てられている**auditusers**ユーザー定義ロールのメンバーである場合は、パッケージに対する読み取りアクセス`db_ssisadmin`権を持つ、、 **db_ssisltduser**、または**db_ssisoperator**ロールのメンバーでもある必要があります。  
  
 ユーザー定義ロールをパッケージに割り当てていない場合、パッケージへのアクセスは固定データベース レベル ロールによって決定されます。  
  
 ユーザー定義ロールを使用する場合は、パッケージに割り当てる前に、 `msdb`データベースに追加する必要があります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、新しいデータベース ロールを作成できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データベース レベルのロールは、msdb データベース内の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] システム テーブルに対する権限を付与します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースエンジンに接続して`msdb`データベースにアクセスするには、事前に (MSSQLSERVER サービス) を開始しておく必要があります。  
  
 パッケージにロールを割り当てるには、次のタスクを完了する必要があります。  
  
-   **オブジェクト エクスプローラーを開いて Integration Services に接続する**  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してパッケージにロールを割り当てるには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーを開き、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に接続する必要があります。  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスを起動してから、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]に接続します。  
  
-   **リーダー ロールおよびライター ロールをパッケージに割り当てる**  
  
     リーダー ロールおよびライター ロールをそれぞれのパッケージに割り当てることができます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [リーダー ロールおよびライター ロールをパッケージに割り当てる](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [ユーザー定義ロールを作成する](../create-a-user-defined-role.md)  
  
-   [Integration Services に接続する](../connect-to-integration-services.md)  
  
  

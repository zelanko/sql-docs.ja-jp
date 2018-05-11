---
title: セキュリティ ロール (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c4e663a005e2c619138b27cffdbe839f9299cd8c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>セキュリティ ロール (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ロールで使用される[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のセキュリティを管理する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]オブジェクトとデータ。 基本的な用語では、ロールは Microsoft Windows ユーザーと特定のアクセス権とアクセス許可のインスタンスによって管理されるオブジェクトの定義を持つグループのセキュリティ識別子 (Sid) を関連付けます。[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 2 つの種類のロールがで提供される[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:  
  
-   サーバー ロール。管理者が [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスにアクセスできるようにするための固定ロールです。  
  
-   データベース ロール。管理者以外のユーザーによるオブジェクトやデータへのアクセスを制御するために、管理者によって定義されるロールです。  
  
 セキュリティの[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]セキュリティは、ロールとアクセス許可を使用して管理します。 ロールはユーザーのグループです。 ユーザー (メンバーとも呼ばれる) はロールに追加したり、ロールから削除したりできます。 オブジェクトに対する権限はロールによって指定されます。ロールのすべてのメンバーは、そのロールが権限を持つオブジェクトを使用できます。 ロールのすべてのメンバーは、オブジェクトに対して等しい権限を持ちます。 権限はオブジェクトに対して適用されます。 各オブジェクトは、そのオブジェクトに対して許可された権限のコレクションを持ちます。複数の異なる権限セットを 1 つのオブジェクトに付与できます。 オブジェクトの権限コレクションに含まれる各権限には、1 つのロールが割り当てられています。  
  
## <a name="role-and-role-member-objects"></a>Role オブジェクトと Role Member オブジェクト  
 ロールは、ユーザー (メンバー) のコレクションを格納するオブジェクトです。 ロールの定義内のユーザーのメンバーシップを確立する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 権限はロールに基づいて割り当てられます。したがって、ユーザーがオブジェクトにアクセスするためには、いずれかのロールのメンバーになる必要があります。  
  
 <xref:Microsoft.AnalysisServices.Role> オブジェクトは、Name、ID、および Members の各パラメーターで構成されます。 Members は文字列のコレクションです。 各メンバーには "domain\username" という形式のユーザー名が含まれます。 Name はロールの名前を表す文字列です。 ID はロールの一意な識別子を表す文字列です。  
  
### <a name="server-role"></a>サーバー ロール  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバーの役割のインスタンスに Windows ユーザーおよびグループの管理アクセス権を定義する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。 このロールのメンバーがすべてにアクセス権を持つ[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースおよびインスタンス上のオブジェクト[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、次のタスクを実行できます。  
  
-   SQL Server Management Studio または [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] を使用して、データベースの作成やサーバーレベルのプロパティの設定など、サーバーレベルの管理機能を実行する。  
  
-   分析管理オブジェクト (AMO) を使用して、プログラムで管理機能を実行する。  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータベース ロールを保守する。  
  
-   トレースを開始する (プロセス アクセス権を持つデータベース ロールによって実行可能な処理イベントを除く)。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の各インスタンスには、そのインスタンスを管理できるユーザーを定義するサーバー ロールがあります。 このロールの名前と ID は Administrators で、データベース ロールとは異なり、サーバー ロールは削除できず、権限を追加または削除することもできません。 つまり、ユーザーはまたはのインスタンスの管理者ではない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]自分がのインスタンスをサーバーの役割に含まれるかどうかに応じて、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
### <a name="database-roles"></a>データベース ロール  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース ロールのオブジェクトとデータにユーザーのアクセスを定義、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。 データベース ロールは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース内に個別のオブジェクトとして作成され、そのロールが作成されたデータベースのみに適用されます。 Windows ユーザーおよびグループは、管理者によってこのロールに含まれています。管理者は、このロール内の権限も定義します。  
  
 ロールの権限は、メンバーがデータベース内のオブジェクトとデータだけでなく、データベース自体にアクセスして管理できるようにするものです。 各権限には 1 つまたは複数のアクセス権が関連付けられており、アクセス権によってデータベース内の特定のオブジェクトへのアクセスをさらに詳細に制御できるようになっています。  
  
## <a name="permission-objects"></a>Permission オブジェクト  
 権限は、各ロールについて、オブジェクト (キューブやディメンションなど) に関連付けられます。 権限は、ロールのメンバーがオブジェクトに対して実行できる操作を指定します。  
  
 <xref:Microsoft.AnalysisServices.Permission> クラスは抽象クラスです。 そのため、対応するオブジェクトに権限を定義するには、派生クラスを使用する必要があります。 オブジェクトごとに権限の派生クラスが定義されます。  
  
|オブジェクト|クラス|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 権限によって使用可能となるアクションを以下の一覧に示します。  
  
|操作|値|説明|  
|------------|------------|-----------------|  
|[処理]|{**true**, **false**}<br /><br /> 既定値 =**false**|**true**を指定した場合、メンバーはこのオブジェクトと、このオブジェクトに含まれる任意のオブジェクトを処理できます。<br /><br /> Process 権限はマイニング モデルには適用されません。 <xref:Microsoft.AnalysisServices.MiningModel> 常に権限の継承元<xref:Microsoft.AnalysisServices.MiningStructure>です。|  
|ReadDefinition|{**None**, **Basic**, **Allowed**}<br /><br /> 既定値 =**None**|オブジェクトに関連付けられたデータ定義 (ASSL) をメンバーが読み取れるかどうかを指定します。<br /><br /> **Allowed**を指定した場合、メンバーはオブジェクトに関連付けられた ASSL を読み取ることができます。<br /><br /> **Basic** および **Allowed** は、オブジェクトに含まれるオブジェクトによって継承されます。 **Allowed** は **Basic** および **None**よりも優先されます。<br /><br /> オブジェクトで DISCOVER_XML_METADATA を使用する場合、**Allowed** を指定する必要があります。 リンク オブジェクトとローカル キューブを作成する場合、**Basic** を指定する必要があります。|  
|読み取り|{**None**, **Allowed**}<br /><br /> 既定値 =**None** (DimensionPermission の場合は、既定値 =**Allowed**)|スキーマ行セットおよびデータ コンテンツへの読み取りアクセスがメンバーにあるかどうかを指定します。<br /><br /> **Allowed** を指定した場合は、データベースへの読み取りアクセスが許可され、データベースを検出できるようになります。<br /><br /> **許可されている**キューブに対する読み取りアクセス スキーマ行セットとアクセスでキューブのコンテンツへ (によって制限しない限り、<xref:Microsoft.AnalysisServices.CellPermission>と<xref:Microsoft.AnalysisServices.CubeDimensionPermission>)。<br /><br /> **許可されている**ディメンション許可ディメンション内のすべての属性に対する権限を読み取ることで (によって制限しない限り、 <xref:Microsoft.AnalysisServices.CubeDimensionPermission>)。 Read (読み取り) 権限は、<xref:Microsoft.AnalysisServices.CubeDimensionPermission> の静的継承でのみ使用されます。 ディメンションに対して**None** を指定した場合は、ディメンションが非表示になり、集計可能な属性への既定のメンバーのアクセスのみが許可されます。ディメンションに集計不能な属性が含まれる場合はエラーが発生します。<br /><br /> **許可されている**上、<xref:Microsoft.AnalysisServices.MiningModelPermission>予測結合を実行するスキーマ行セット内のオブジェクトを表示するアクセス許可を付与します。<br /><br /> **NoteAllowed**がデータベース内のオブジェクトに対する読み取りまたは書き込みに必要です。|  
|Write|{**None**, **Allowed**}<br /><br /> 既定値 =**None**|親オブジェクトのデータへの書き込みアクセスがメンバーにあるかどうかを指定します。<br /><br /> <xref:Microsoft.AnalysisServices.Dimension>、<xref:Microsoft.AnalysisServices.Cube>、および <xref:Microsoft.AnalysisServices.MiningModel> の各サブクラスにアクセスが適用されます。 データベースには適用されません<xref:Microsoft.AnalysisServices.MiningStructure>サブクラスで、検証エラーが発生します。<br /><br /> **許可されている**上、<xref:Microsoft.AnalysisServices.Dimension>ディメンション内のすべての属性に対する書き込み権限が許可されます。<br /><br /> **許可されている**上、<xref:Microsoft.AnalysisServices.Cube>型として定義されたパーティションに対するキューブのセルに対する権限を書き込み許可書き戻しを = です。<br /><br /> **許可されている**上、<xref:Microsoft.AnalysisServices.MiningModel>モデルの内容を変更する権限を付与します。<br /><br /> **許可されている**上、<xref:Microsoft.AnalysisServices.MiningStructure>特定の意味を持たない[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。<br /><br /> 注: 書き込みに設定することはできません**許可**読み取りも設定しない限り、**許可**|  
|Administer<br /><br /> 注: のみのデータベースのアクセス許可|{**true**, **false**}<br /><br /> 既定値 =**false**|メンバーがデータベースを管理できるかどうかを指定します。<br /><br /> **true** を指定した場合は、データベース内のすべてのオブジェクトへのアクセスが許可されます。<br /><br /> メンバーは特定のデータベースに対してのみ管理権限を持つことができます。他のデータベースを管理することはできません。|  
  
## <a name="see-also"></a>参照  
 [アクセス許可とアクセス権と #40 です。Analysis Services - 多次元データ & #41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [オブジェクトと操作 & #40; への認証のアクセスAnalysis Services & #41;](../../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  

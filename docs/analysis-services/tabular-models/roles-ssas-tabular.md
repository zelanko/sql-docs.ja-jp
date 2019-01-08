---
title: Analysis Services 表形式モデルのロール |Microsoft Docs
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bbbf4f080696d41360e7fd654ef4b6878df268a6
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072169"
---
# <a name="roles"></a>ロール
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブル モデルでは、ロールはあるモデルのメンバー アクセス許可を定義します。 ロールのメンバーは、ロール権限によって定義されたとおりにモデル上で各種操作を実行できます。 読み取り権限を付与して定義されたロールでは、行レベル フィルターを使用して行レベルでのセキュリティを向上させることもできます。 
  
 SQL Server の Analysis Services の役割には、Windows ユーザー名または Windows グループ、およびアクセス許可 (読み取り、処理、管理者) にユーザーのメンバーが含まれます。 Azure Analysis services では、ユーザーは、Azure Active Directory とユーザー名である必要があり、指定されたグループは、組織の電子メール アドレスまたは UPN である必要があります。 

> [!IMPORTANT]  
>  ときに SSDT を使用してロールを作成し、表形式モデルに組織のユーザーがプロジェクトに追加展開する Azure Analysis Services を使用して[統合ワークスペース](workspace-database-ssas-tabular.md)します。

> [!IMPORTANT]  
>  ユーザーがレポート クライアント アプリケーションを使用して配置済みモデルへの接続に、作成する必要がで少なくとも 1 つのロールには少なくとも読み取りアクセス許可には、それらのユーザーがのメンバー。  
  
 このトピックの情報は、SSDT でロール マネージャー ダイアログ ボックスを使用してロールを定義するテーブル モデル作成者向けです。 モデル作成時に定義されたロールは、モデル ワークスペース データベースに適用されます。 Model データベースが配置された後モデル データベース管理者を管理できます (追加、編集、削除) SSMS を使用してロールのメンバー。 デプロイされたデータベース内のロールのメンバーの管理については、次を参照してください。[テーブル モデル ロール](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md)します。  
  
##  <a name="bkmk_underst"></a> Understanding roles  
 ロールは、Analysis Services でモデル データ アクセスの管理に使用されます。 ロールには次の 2 種類があります。  
  
-   サーバー ロール、固定ロール管理者、Analysis Services サーバー インスタンスへのアクセスを提供します。  
  
-   データベース ロール。管理者以外のユーザーによるモデル データベースとデータへのアクセスを制限するために、モデル作成者と管理者によって定義されるロールです。  
  
 テーブル モデル向けに定義されているロールは、データベース ロールです。 つまり、ロールのユーザーで構成されるメンバーを含めることがまたはをそれらのメンバーにアクションを定義する特定のアクセス許可を持つグループが、モデル データベースに対して実行できます。 データベース ロールは、データベース内に個別のオブジェクトとして作成され、そのロールが作成されたデータベースのみに適用されます。 ユーザーとグループを既定では、ワークスペース データベース サーバーで管理者のアクセス許可を持つモデル作成者が、ロール内に含まれる管理者がの配置済みモデル。  
  
 テーブル モデルでのロールは、行フィルターでさらに定義できます。 行フィルターでは、DAX 式を使用して、テーブル内の行とユーザーがクエリを実行できる多くの方向の関連行を定義します。 DAX 式を使用する行フィルターを定義できるのは、読み取りおよび読み取りと処理の権限に対してだけです。 詳細についてを参照してください。[行フィルター](#bkmk_rowfliters)このトピックで後述します。  
  
 既定では、テーブル モデル プロジェクトの新規作成時点では、モデル プロジェクトにロールはありません。 SSDT でロール マネージャー ダイアログ ボックスを使用してロールを定義できます。 モデルを作成しているときにロールを定義すると、それらのロールはモデル ワークスペース データベースに適用されます。 モデルを配置すると、同じロールが配置済みモデルに適用されます。 モデルを配置すると後のメンバー サーバーの役割 ([Analysis Services の管理者) とデータベース管理者は、モデルに関連付けられているロールと SSMS を使用して、各ロールに関連付けられているメンバーを管理できます。  
  
##  <a name="bkmk_permissions"></a> Permissions  
 各ロールに定義済みデータベース権限が 1 つ存在します (読み取りと処理を組み合わせた権限を除きます)。 既定では、新しいロールの権限は [なし] です。 つまり、メンバーが権限のないロールに追加されると、別の権限が与えられるまで、データベースの変更、処理操作の実行、データの照会、およびデータベースの表示を行うことはできません。  
  
 グループまたはユーザーは、任意の数のロールでは、さまざまなアクセス許可を持つ各ロールのメンバーであることができます。 ある 1 人のユーザーが、複数個のロールのメンバーである場合、各ロールに対して定義された権限は累積されます。 たとえば、あるユーザーが読み取り権限を持つロールのメンバーであると同時に、権限のないロールのメンバーでもある場合、そのユーザーは読み取り権限を持つことになります。  
  
 各ロールに対して、次のうちいずれかの権限を定義できます。  
  
|アクセス許可|説明|DAX を使用する行フィルター|  
|-----------------|-----------------|----------------------------|  
|なし|メンバーは、モデルのデータベース スキーマを変更したり、データを照会したりすることはできません。|行フィルターは適用されません。 このロールのユーザーには、データは表示されません。|  
|Read|メンバーは、(行フィルターに基づいて) データに対してクエリを実行できますが、SSMS のモデル データベースを表示することはできず、モデルのデータベース スキーマを変更することはできません。また、ユーザーはモデルを処理できません。|行フィルターが適用されます。 行フィルター DAX 式で指定されたデータのみがユーザーに表示されます。|  
|読み取りと処理|メンバーは、(行レベル フィルターに基づいて) データを照会でき、処理コマンドを埋め込んだパッケージまたはスクリプトを実行することで処理操作を実行できますが、データベースを変更することはできません。 SSMS で、モデル データベースを表示することはできません。|行フィルターが適用されます。 行フィルター DAX 式で指定されたデータのみ照会できます。|  
|[処理]|メンバーは、処理コマンドを埋め込んだパッケージまたはスクリプトを実行することで、処理操作を実行できます。 モデルのデータベース スキーマを変更することはできません。 データを照会することはできません。 SSMS のモデル データベースをクエリすることはできません。|行フィルターは適用されません。 この役割ではデータを照会できません。|  
|管理者|メンバーは、モデルのスキーマに変更を加えることができ、モデル デザイナー、レポート クライアント、および SSMS のすべてのデータをクエリすることができます。|行フィルターは適用されません。 この役割ではすべてのデータを照会することはできません。|  
  
##  <a name="bkmk_rowfliters"></a> Row filters  
 行フィルターは、特定のロールのメンバーが照会できるテーブル内の行を定義します。 行フィルターは、DAX 式を使用してモデル内の各テーブルに対して定義されます。  
  
 行フィルターを定義できるのは、読み取りおよび読み取りと処理の権限を持つロールに対してだけです。 既定では、ある特定のテーブルに対して行フィルターが定義されていない場合、読み取り権限または読み取りと処理の権限を持つロールのメンバーは、別のテーブルからのクロスフィルター処理が適用されていない限り、テーブル内のすべての行を照会できます。  
  
 ある特定のテーブルに対して行フィルターが定義されると、DAX 式 (これは TRUE/FALSE 値に評価される必要がある) によりその特定のロールのメンバーが照会できる行が定義されます。 DAX 式に含まれていない行は照会できません。 たとえば、Sales ロールのメンバーの場合、次の行を持つ Customers テーブル フィルター、式、 *= Customers [Country] ="USA"*、Sales ロールのメンバーは、米国内の顧客を参照してください。 できます。  
  
 行フィルターは、指定行と関連行に適用されます。 1 つのテーブルに複数のリレーションシップがある場合、フィルターによりセキュリティがアクティブなリレーションシップに適用されます。 行フィルターには、関連テーブルに対して定義された他の行フィルターと類似する点があります。次に例を示します。  
  
|テーブル|DAX 式|  
|-----------|--------------------|  
|Region|= リージョン [Country] ="USA"|  
|ProductCategory|= ProductCategory [Name]「自転車」を =|  
|トランザクション|=Transactions[Year]=2008|  
  
 Transactions テーブルに対するこれらの権限の実質的な影響は、顧客が米国内に存在し、製品カテゴリが自転車で、しかも年度が 2008 であるデータ行をメンバーが照会できることです。 メンバーは、顧客が米国外にいるか、製品が自転車でないか、または年度が 2008 年でないトランザクションは照会できません。ただし、これらの権限を付与された別のロールのメンバーである場合を除きます。  
  
 *=FALSE()* というフィルターを使用すると、テーブル全体のすべての行に対するアクセスを拒否することができます。  
  
### <a name="dynamic-security"></a>動的なセキュリティ  
 動的なセキュリティには、現在ログオンしているユーザーの名前、または接続文字列から返された CustomData プロパティに基づいて、行レベルのセキュリティを定義する方法が用意されています。 動的なセキュリティを実装するために、ユーザーのログイン値 (Windows ユーザー名) および特定の権限を定義できるフィールドを含むテーブルをモデルに含める必要があります。たとえば、ログイン ID (domain\username) と、各従業員の部署の値を含む dimEmployees テーブルなどです。  
  
 動的なセキュリティを実装する場合、DAX 式に次の関数を使用すると、現在ログオンしているユーザーの名前、または接続文字列の CustomData プロパティが返されます。  
  
|関数|説明|  
|--------------|-----------------|  
|[USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)|現在ログオンしているユーザーの domain\username を返します。|  
|[CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/58235ad8-226c-43cc-8a69-5a52ac19dd4e)|接続文字列の CustomData プロパティを返します。|  
  
 LOOKUPVALUE 関数を使用すると、USERNAME 関数で返されるユーザー名または CustomData 関数で返される文字列と同じ Windows ユーザー名を含む列の値が返されます。 同じテーブルまたは関連テーブルの中で、LOOKUPVALUE で返された値と一致する値だけが照会されるように制限できます。  
  
 たとえば、次の式を使用します。  
  
 `='dimDepartmentGroup'[DepartmentGroupId]=LOOKUPVALUE('dimEmployees'[DepartmentGroupId], 'dimEmployees'[LoginId], USERNAME(), 'dimEmployees'[LoginId], 'dimDepartmentGroup'[DepartmentGroupId])`  
  
 この LOOKUPVALUE 関数では、USERNAME で返される現在ログオンしているユーザーの LoginID と同じ dimEmployees[LoginId] を持つ dimEmployees[DepartmentId] 列の値が返されます。dimEmployees[DepartmentId] と dimDepartmentGroup[DepartmentId] の値は同じです。 次に、LOOKUPVALUE で返された DepartmentId の値を使用して、dimDepartment テーブル、および DepartmentId で関連付けられたすべてのテーブルで、クエリ対象の行を制限します。 LOOKUPVALUE 関数で返された DepartmentId の値にも含まれる DepartmentId を持つ行だけが返されます。  
  
 **dimEmployees**  
  
|LastName|FirstName|LoginID|DepartmentName|DepartmentId|  
|--------------|---------------|-------------|--------------------|------------------|  
|Brown|Kevin|Adventure-works\kevin0|マーケティング|7|  
|Bradley|David|Adventure-works\david0|マーケティング|7|  
|Dobney|JoLynn|Adventure-works\JoLynn0|Production|4|  
|Baretto DeMattos|Paula|Adventure-works\Paula0|Human Resources|2|  
  
 **dimDepartment**  
  
|DepartmentId|DepartmentName|  
|------------------|--------------------|  
|1|Corporate|  
|2|Executive General and Administration|  
|3|Inventory Management|  
|4|Manufacturing|  
|5|Quality Assurance|  
|6|Research and Development|  
|7|Sales and Marketing|  
  
##  <a name="bkmk_testroles"></a> Testing roles  
 モデル プロジェクトの作成時に、Excel で分析機能を使用して、定義したロールの有効性をテストできます。 モデル デザイナーで **[モデル]** メニューの **[Excel で分析]** をクリックすると、Excel が開く前に **[資格情報とパースペクティブの選択]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、データ ソースとしてワークスペース モデルに接続するために使用する、現在のユーザー名、別のユーザー名、ロール、およびパースペクティブを指定できます。 詳細については、「 [[Excel で分析]](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)と同じコンピューター上に Excel がインストールされている必要があります。  
  
##  <a name="bkmk_rt"></a> 関連タスク  
  
|トピック|説明|  
|-----------|-----------------|  
|[ロールの作成および管理](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)|このトピックのタスクでは、 **[ロール マネージャー]** ダイアログ ボックスを使用して、ロールを作成し管理する方法について説明されています。|  
  
## <a name="see-also"></a>参照  
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [[Excel で分析]](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [USERNAME 関数 (DAX)](http://msdn.microsoft.com/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [LOOKUPVALUE 関数 (DAX)](http://msdn.microsoft.com/73a51c4d-131c-4c33-a139-b1342d10caab)   
 [CUSTOMDATA 関数 (DAX)](http://msdn.microsoft.com/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  

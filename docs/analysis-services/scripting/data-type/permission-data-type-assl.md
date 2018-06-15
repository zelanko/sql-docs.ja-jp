---
title: Permission データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a7e400a8fbdca47ff678e8b02c89064771c9450
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033303"
---
# <a name="permission-data-type-assl"></a>Permission データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  個別の権限についての情報を表す抽象プリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)、 [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)、 [DimensionPermission](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md)、 [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[プロセス](../../../analysis-services/scripting/properties/process-element-assl.md)、[読み取り](../../../analysis-services/scripting/properties/read-element-assl.md)、 [ReadDefinition](../../../analysis-services/scripting/properties/readdefinition-element-assl.md)、 [RoleID](../../../analysis-services/scripting/properties/roleid-element-assl.md)、[書き込み](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>解説  
 **アクセス許可**、抽象基本型のインスタンスで使用される権限の派生型の数の役割を果たす[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 DeploymentMode の値が 2 (テーブル サーバー モード) の場合、このデータ型には次の検証が適用されます。  
  
-   *プロセス*に属性の既定値が設定されている**False**、ユーザーが持っている場合を除き、**更新**権限です。 持つユーザー、**更新**権限、*プロセス*に属性値が設定されている**True**です。  
  
-   *ReadDefinition*に属性値が設定されている**None**; その他の値、エラーが発生します。  
  
-   *読み取り*に属性値が設定されている**許可**を持つユーザー、**ユーザー**権限および**なし**にユーザーが割り当てられるとき、 **更新**権限以外のかどうか、ユーザーが両方とも**ユーザー**と**更新**アクセス権、その属性に設定されている**許可**です。 管理者特権を持つユーザーの属性値に設定**許可**です。  
  
-   *書き込み*に属性値が設定されている**None**; その他の値、エラーが発生します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

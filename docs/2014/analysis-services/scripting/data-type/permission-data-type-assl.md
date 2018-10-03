---
title: Permission データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Permission Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Permission
helpviewer_keywords:
- Permission data type
ms.assetid: 5f309544-59f8-4432-b1eb-b7c1a049f8df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8d12fb71a8ed19ca083e8ec506fba6338f6b58a7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101944"
---
# <a name="permission-data-type-assl"></a>Permission データ型 (ASSL)
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
|派生データ型|[CubePermission](../objects/cubepermission-element-assl.md)、 [DatabasePermission](../objects/databasepermission-element-assl.md)、 [DimensionPermission](permission-data-type-assl.md)、 [MiningModelPermission](../objects/miningmodelpermission-element-assl.md)、 [MiningStructurePermission](../objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [名](../properties/name-element-assl.md)、[プロセス](../properties/process-element-assl.md)、[読み取り](../properties/read-element-assl.md)、 [ReadDefinition](../properties/readdefinition-element-assl.md)、 [RoleID](../properties/roleid-element-assl.md)、[書き込み](../properties/write-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Permission` 多くのインスタンスで使用されるアクセス許可の派生型の抽象基本型として機能[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 DeploymentMode の値が 2 (テーブル サーバー モード) の場合、このデータ型には次の検証が適用されます。  
  
-   *プロセス*属性の既定値に設定されます`False`、ユーザーが持っている場合を除き、**更新**権限。 持つユーザー、**更新**アクセス許可、*プロセス*属性の値に設定されて`True`します。  
  
-   *ReadDefinition*属性の値に設定されて`None`; その他の値には、エラーが生成されます。  
  
-   *読み取り*属性の値に設定されて`Allowed`を持つユーザー、**ユーザー**権限および`None`に、ユーザーが割り当てられるとき、**更新**アクセス許可はどちらもユーザーが持っています。**ユーザー**と**更新**アクセス許可は、その属性が設定されている場合`Allowed`します。 管理者権限を持つユーザーの属性値は `Allowed` に設定されます。  
  
-   *書き込み*属性の値に設定されて`None`; その他の値には、エラーが生成されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

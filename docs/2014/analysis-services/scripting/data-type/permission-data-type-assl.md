---
title: Permission データ型 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff5fb67e4f7989fb329e60a106ea8e6d0c734c97
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071266"
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
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[説明](../properties/description-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[名前](../properties/name-element-assl.md)、[プロセス](../properties/process-element-assl.md)、[読み取り](../properties/read-element-assl.md)、 [ReadDefinition](../properties/readdefinition-element-assl.md)、 [RoleID](../properties/roleid-element-assl.md)、[書き込み](../properties/write-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Permission` インスタンスで使用される権限の派生型の数の抽象基本型の役割を果たす[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 DeploymentMode の値が 2 (テーブル サーバー モード) の場合、このデータ型には次の検証が適用されます。  
  
-   *プロセス*に属性の既定値が設定されている`False`、ユーザーが持っている場合を除き、**更新**権限です。 持つユーザー、**更新**権限、*プロセス*に属性値が設定されている`True`です。  
  
-   *ReadDefinition*に属性値が設定されている`None`; その他の値、エラーが発生します。  
  
-   *読み取り*に属性値が設定されている`Allowed`を持つユーザー、**ユーザー**権限および`None`にユーザーが割り当てられるとき、**更新**権限以外の場合は、ユーザーが、両方を持つかどうか**ユーザー**と**更新**アクセス権、その属性に設定されている`Allowed`です。 管理者権限を持つユーザーの属性値は `Allowed` に設定されます。  
  
-   *書き込む*に属性値が設定されている`None`; その他の値、エラーが発生します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Permission>します。  
  
## <a name="see-also"></a>参照  
 [Role 要素&#40;ASSL&#41;](../objects/role-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
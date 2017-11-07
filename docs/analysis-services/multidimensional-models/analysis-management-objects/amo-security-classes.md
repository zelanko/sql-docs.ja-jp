---
title: "AMO セキュリティ クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b61917a7e0191e1645dedef69a311a8f901d12b9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="amo-security-classes"></a>AMO セキュリティ クラス
  このトピックには、次のセクションが含まれます。  
  
-   [Role オブジェクトと RoleMember オブジェクト](#RolesMembers)  
  
-   [Permission オブジェクト](#Permissions)  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![Amo セキュリティ クラスは、このトピックで説明](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-securityclasses.gif "amo セキュリティ クラスは、このトピックの内容")  
  
##  <a name="RolesMembers"></a>Role オブジェクトと RoleMember オブジェクト  
 <xref:Microsoft.AnalysisServices.Role> オブジェクトを作成するには、データベースのロール コレクションに新しいオブジェクトを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Role> オブジェクトを更新します。 <xref:Microsoft.AnalysisServices.Role> オブジェクトは使用する前に更新する必要があります。  
  
 削除する、<xref:Microsoft.AnalysisServices.Role>オブジェクトの Drop メソッドを使用して、削除する必要がある、<xref:Microsoft.AnalysisServices.Role>オブジェクト。 Remove メソッドを使用してロールをロール コレクションから削除しても、アプリケーションでロールが見えなくなるだけで、サーバーからは削除されません。 <xref:Microsoft.AnalysisServices.Role> オブジェクトに権限が関連付けられている場合は、このオブジェクトを削除できません。  
  
 <xref:Microsoft.AnalysisServices.RoleMember> オブジェクトを作成するには、ロールのメンバー コレクションにユーザーを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Role> オブジェクトを更新します。 ロールを作成できるのは、Server Administrators または Database Administrators だけです。 オブジェクトへの権限が付与され任意のたメンバーに対しそのオブジェクトの使用を許可する前に、<xref:Microsoft.AnalysisServices.Role> オブジェクトをサーバー上で更新する必要があります。  
  
 <xref:Microsoft.AnalysisServices.RoleMember> オブジェクトを削除する場合は、コレクションの Remove メソッドを使用してコレクションからこれを削除し、Update メソッドを使用してロールを更新する必要があります。  
  
 これらのオブジェクトで使用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Role>」の「<xref:Microsoft.AnalysisServices.RoleMember>」および「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="Permissions"></a>Permission オブジェクト  
 <xref:Microsoft.AnalysisServices.Permission> オブジェクトを作成するには、オブジェクトの権限コレクションに新しい権限オブジェクトを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Permission> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.Permission> オブジェクトを削除する場合は、このオブジェクトの Drop メソッドを使用します。 Remove メソッドを使用して権限を権限コレクションから削除しても、アプリケーションで権限が見えなくなるだけで、<xref:Microsoft.AnalysisServices.Permission> オブジェクトはサーバーから削除されません。 ロールに関連付けられた権限が存在する場合は、ロールを削除できません。  
  
 メソッドおよび使用可能なプロパティの詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.Permission>で<xref:Microsoft.AnalysisServices>です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO セキュリティ オブジェクトのプログラミング](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-security-objects.md)   
 [アクセス許可とアクセス権と #40 です。Analysis Services - 多次元データ &#41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  


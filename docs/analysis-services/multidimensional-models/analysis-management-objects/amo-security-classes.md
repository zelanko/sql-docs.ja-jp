---
title: AMO セキュリティ クラス |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ca8bf233f706883b29c518517a28216e144765d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023349"
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
 [アクセス許可とアクセス権と #40 です。Analysis Services - 多次元データ & #41;](http://msdn.microsoft.com/library/59fa3573-f985-46cb-8042-7da71bd59a7b)   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

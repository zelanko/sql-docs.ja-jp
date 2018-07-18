---
title: AMO セキュリティ クラス |Microsoft Docs
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
helpviewer_keywords:
- Analysis Management Objects, security
- security [AMO]
- AMO, security
ms.assetid: e3d5012a-8121-40de-9244-1fc824228693
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de0adbcc122e87ef95a349b357f0cfd173bd98a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220292"
---
# <a name="amo-security-classes"></a>AMO セキュリティ クラス
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![AMO セキュリティ クラスは、このトピックで説明](../../../analysis-services/dev-guide/media/amo-securityclasses.gif "AMO セキュリティ クラスは、このトピックで説明")  
  
##  <a name="RolesMembers"></a> Role オブジェクトと RoleMember オブジェクト  
 <xref:Microsoft.AnalysisServices.Role> オブジェクトを作成するには、データベースのロール コレクションに新しいオブジェクトを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Role> オブジェクトを更新します。 <xref:Microsoft.AnalysisServices.Role> オブジェクトは使用する前に更新する必要があります。  
  
 削除する、<xref:Microsoft.AnalysisServices.Role>オブジェクトの Drop メソッドを使用して削除する必要がある、<xref:Microsoft.AnalysisServices.Role>オブジェクト。 Remove メソッドを使用してロールをロール コレクションから削除しても、アプリケーションでロールが見えなくなるだけで、サーバーからは削除されません。 <xref:Microsoft.AnalysisServices.Role> オブジェクトに権限が関連付けられている場合は、このオブジェクトを削除できません。  
  
 <xref:Microsoft.AnalysisServices.RoleMember> オブジェクトを作成するには、ロールのメンバー コレクションにユーザーを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Role> オブジェクトを更新します。 ロールを作成できるのは、Server Administrators または Database Administrators だけです。 オブジェクトへの権限が付与され任意のたメンバーに対しそのオブジェクトの使用を許可する前に、<xref:Microsoft.AnalysisServices.Role> オブジェクトをサーバー上で更新する必要があります。  
  
 <xref:Microsoft.AnalysisServices.RoleMember> オブジェクトを削除する場合は、コレクションの Remove メソッドを使用してコレクションからこれを削除し、Update メソッドを使用してロールを更新する必要があります。  
  
 これらのオブジェクトで使用可能なメソッドおよびプロパティの詳細については、「<xref:Microsoft.AnalysisServices.Role>」の「<xref:Microsoft.AnalysisServices.RoleMember>」および「<xref:Microsoft.AnalysisServices>」を参照してください。  
  
##  <a name="Permissions"></a> アクセス許可オブジェクト  
 <xref:Microsoft.AnalysisServices.Permission> オブジェクトを作成するには、オブジェクトの権限コレクションに新しい権限オブジェクトを追加し、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.Permission> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.Permission> オブジェクトを削除する場合は、このオブジェクトの Drop メソッドを使用します。 Remove メソッドを使用して権限を権限コレクションから削除しても、アプリケーションで権限が見えなくなるだけで、<xref:Microsoft.AnalysisServices.Permission> オブジェクトはサーバーから削除されません。 ロールに関連付けられた権限が存在する場合は、ロールを削除できません。  
  
 メソッドと使用可能なプロパティの詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.Permission>で<xref:Microsoft.AnalysisServices>します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO セキュリティ オブジェクトのプログラミング](programming-amo-security-objects.md)   
 [アクセス許可とアクセス権&#40;Analysis Services - 多次元データ&#41;](https://msdn.microsoft.com/library/ms174786(v=sql.120).aspx)   
 [AMO クラスの概要](amo-classes-introduction.md)   
 [論理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト&#40;Analysis Services - 多次元データ&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

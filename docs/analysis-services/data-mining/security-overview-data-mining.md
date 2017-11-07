---
title: "セキュリティの概要 (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Analysis Services - data mining], about security
ms.assetid: 387bde00-bcf3-4612-b27b-f9f608dbf71e
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4857608190aa03baca0a6916275641f463c6cf2a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview-data-mining"></a>セキュリティの概要 (データ マイニング)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のセキュリティ保護は、複数レベルで行われます。 まず [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の各インスタンスと、そのデータ ソースのセキュリティを保護して、認証されたユーザーのみが、選択されたディメンション、マイニング モデル、およびデータ ソースに対する読み取り、または読み取り/書き込み権限を持つことを確認する必要があります。 基になるデータ ソースのセキュリティを保護して、権限のないユーザーが機密のビジネス情報を悪意で危険にさらすことを防ぐ必要もあります。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスのセキュリティを保護するプロセスは、次のトピックで説明しています。  
  
##  <a name="bkmk_Architecture"></a> セキュリティのアーキテクチャ  
 次のリソースを参照して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Windows 認証を使用してユーザーのアクセスを認証する方法なども含めて、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] のインスタンスの基本的なセキュリティ アーキテクチャを理解してください。  
  
-   [セキュリティ ロール (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
-   [セキュリティのプロパティ](../../analysis-services/server-properties/security-properties.md)  
  
-   [サービス アカウントの構成 (Analysis Services)](../../analysis-services/instances/configure-service-accounts-analysis-services.md)  
  
-   [オブジェクトと操作へのアクセスの承認 (Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)  
  
##  <a name="bkmk_Logon"></a> Analysis Services のログオン アカウントの構成  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に対して適切なログオン アカウントを選択し、このアカウントの権限を指定する必要があります。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログオン アカウントには、基になるデータ ソースへの適切な権限を含め、必要なタスクの実行に要する権限のみが与えられていることを確認する必要があります。  
  
 データ マイニングでは、モデルを作成して処理する場合と、モデルを表示またはクエリする場合で必要な権限セットが異なります。 モデルに対する予測の作成は一種のクエリなので、管理権限は必要ありません。  
  
##  <a name="bkmk_Instance"></a> Analysis Services インスタンスのセキュリティ保護  
 次に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンピューター、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンピューター上の Windows オペレーティング システム、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 自体、およびその [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が使用するデータ ソースのセキュリティを保護する必要があります。  
  
##  <a name="bkmk_Access"></a> Analysis Services へのアクセスの構成  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスの認証ユーザーを設定および定義する際は、特定のデータベース オブジェクトの管理権限も持つ必要があるユーザー、オブジェクトの定義の表示やモデルの参照を実行できるユーザー、およびデータ ソースに直接アクセスできるユーザーを決定する必要があります。  
  
##  <a name="bkmk_DMspecial"></a> データ マイニングに関する注意事項  
 アナリストや開発者がデータ マイニング モデルを作成およびテストできるようにするには、そのアナリストや開発者に、マイニング モデルが格納されているデータベースに対する管理権限を与える必要があります。 その結果、このデータ マイニング アナリストや開発者は、他のアナリストまたは開発者が作成して使用しているデータ マイニング オブジェクトや、データ マイニング ソリューションに含まれていない OLAP オブジェクトなど、データ マイニングに無関係な他のオブジェクトを作成または削除できる場合があります。  
  
 したがって、データ マイニング用のソリューションを作成する際は、アナリストや開発者がモデルの開発、テスト、およびチューニングを行う必要性と、他のユーザーによるその必要性とのバランスを取り、既存のデータベース オブジェクトを保護する手段を講じる必要があります。 この手段としては、データ マイニング専用の独立したデータベースを作成するか、アナリストごとに個別のデータベースを作成することが考えられます。  
  
 モデルの作成には最高レベルの権限が必要ですが、処理、参照、クエリなど他の操作については、ロール ベースのセキュリティを使用してデータ マイニング モデルに対するユーザーのアクセスを制御できます。 ロールを作成する場合は、データ マイニング オブジェクトに固有の権限を設定します。 ロールのメンバーであるユーザーには、そのロールに関連付けられたすべての権限が自動的に与えられます。  
  
 さらに、データ マイニング モデルでは、機密情報が含まれているデータ ソースを参照することがよくあります。 ユーザーがモデルから構造のデータへドリルスルーできるようにマイニング構造とマイニング モデルが構成されている場合は、機密情報をマスクしたり、基になるデータにアクセスできるユーザーを制限したりするために予防策をとる必要があります。  
  
 Integration Services パッケージを使用してデータのクリーンアップ、マイニング モデルの更新、または予測の作成を行う場合は、モデルが格納されているデータベースに対する適切な権限、およびソース データに対する適切な権限が Integration Services サービスにあることを確認する必要があります。  
  
## <a name="see-also"></a>参照  
 [ロールと権限 (Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  


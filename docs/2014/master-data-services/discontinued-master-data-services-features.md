---
title: SQL Server 2014 | のマスターデータサービス廃止された機能Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3f1eb85cb05c8284990d46241ed752515ef5504b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479441"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a>SQL Server 2014 で提供が中止されたマスター データ サービス機能
  このトピックでは、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] で使用できなくなった [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の機能について説明します。  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 提供が中止された機能  
 今回のリリースで提供が中止された機能はありません。  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 提供が中止された機能  
  
### <a name="security"></a>Security  
 セキュリティの割り当てを簡単にするために、モデル オブジェクト権限を派生階層、明示的階層、および属性グループの各オブジェクトに割り当てることができなくなりました。  
  
-   派生階層権限は、モデルに基づくようになりました。 たとえば、派生階層に対する権限をユーザーに付与するには、モデルオブジェクトに**更新**を割り当てる必要があります。 その後、ユーザーにアクセスを許可しないエンティティに対して、**拒否**アクセス権を割り当てることができます。  
  
-   明示的階層権限は、エンティティに基づくようになりました。 たとえば、ユーザーが Account エンティティに対する**更新**権限を持っている場合、そのエンティティのすべての明示的階層が更新可能になります。  
  
-   [**ユーザー/グループの権限**] 機能領域では、属性グループの権限を割り当てることができなくなりました。 代わりに、属性グループが作成される [**システム管理**] 機能領域で、ユーザーとグループに属性グループに対する**更新**権限を付与することができます。 属性グループに対する**読み取り**専用権限は使用できなくなりました。  
  
### <a name="staging-process"></a>ステージング処理  
 新しいステージング処理を使用して、次の操作を実行することはできません。  
  
-   コレクションの作成または削除。  
  
-   コレクションへのメンバーの追加またはコレクションからのメンバーの削除。  
  
-   メンバーまたはコレクションの再アクティブ化。  
  
 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] のステージング処理を使用して、コレクションを操作できます。  
  
### <a name="model-deployment-wizard"></a>モデル配置ウィザード  
 データを含むパッケージは、ウィザードを使用して [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションに作成および配置することができなくなりました。 代わりに、新しいコマンド ライン ユーティリティを使用することができます。 詳細については、「[モデルの配置 (マスター データ サービス)](deploying-models-master-data-services.md)」を参照してください。  
  
 このウィザードは、データを含まないパッケージの作成および配置には引き続き使用できます。  
  
 また、パッケージは作成されたエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のみで展開できます。 つまり、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] で作成されたパッケージを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に配置することはできません。 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 環境にパッケージを展開してから、データベースを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] にアップグレードする必要があります。  
  
### <a name="code-generation-business-rules"></a>コード生成のビジネス ルール  
 Code 属性の値を自動的に生成するビジネス ルールを管理する方法が変わりました。 以前は、Code 属性の値を生成するために、[**システム管理**] 機能領域の [**ビジネスルール**] の [生成された値] アクション**に既定の属性を**使用しました。 ここで、**システム管理**で、エンティティを編集して、自動的に生成されたコード値を有効にする必要があります。 詳細については、「[自動コード作成 &#40;マスターデータサービス&#41;](automatic-code-creation-master-data-services.md)」を参照してください。  
  
 この種類のルールが格納された [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] モデルの配置パッケージを持っている場合は、データベースを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] にアップグレードすると、ビジネス ルールが除外されます。  
  
### <a name="bulk-updates-and-exporting"></a>一括更新と一括エクスポート  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで、複数のメンバーの属性値を一括更新することができなくなりました。 一括更新を行うには、ステージング処理また[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]はを使用します。  
  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで、メンバーを Excel にエクスポートできなくなりました。 Excel でメンバーを操作するには[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]、を使用します。  
  
### <a name="transactions"></a>トランザクション  
 [**エクスプローラー** ] 機能領域では、ユーザーは自分のトランザクションを元に戻すことができなくなります。 以前は、ユーザーは**エクスプローラー**でデータに対して行った変更を元に戻すことができました。 管理者は、[**バージョン管理**] 機能領域のすべてのユーザーのトランザクションを元に戻すこともできます。  
  
 注釈が永続的に保持されるようになり、削除できなくなりました。 以前は、注釈はトランザクションと見なされていて、トランザクションを元に戻すことで削除できました。  
  
### <a name="web-service"></a>Web サービス  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サービスが、Silverlight の必要に応じて自動的に有効にされるようになりました。 以前は、Web サービスは手動で有効にする必要がありました。  
  
### <a name="powershell-cmdlets"></a>PowerShell コマンドレット  
 MDS に PowerShell コマンドレットが含まれなくなりました。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 に含まれている非推奨のマスター データ サービス機能](deprecated-master-data-services-features.md)  
  
  

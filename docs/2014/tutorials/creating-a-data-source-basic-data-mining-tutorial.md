---
title: データ ソース (基本的なデータ マイニング チュートリアル) を作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ca60870200473b80f114e17db2222d18f5219fba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312722"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>データ ソースの作成 (基本的なデータ マイニング チュートリアル)
  A*データソース*保存し、プロジェクトで管理されに展開されるデータ接続、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。 データ ソースには、ソース データが存在するサーバーとデータベースの名前、および接続に必要なその他のプロパティが含まれます。  
  
> [!IMPORTANT]  
>  データベースの名前は [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] です。 このデータベースをまだインストールがいない場合は、次を参照してください。、 [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417)ページ。  
  
### <a name="to-create-a-data-source"></a>データ ソースを作成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、**データソース**フォルダーと選択**新しいデータ ソース**。  
  
2.  **データ ソース ウィザードへようこそ**] ページで [**次**します。  
  
3.  **接続の定義方法を選択します**] ページで [**新規**への接続を追加する、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベース。  
  
4.  **プロバイダー**の一覧で**接続マネージャー**、**ネイティブ OLE db \sql Server Native Client 11.0**。  
  
5.  **サーバー名**ボックスで、入力するか、インストールしたサーバーの名前を選択[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]します。  
  
     たとえば、「 **localhost**データベースがローカル サーバーでホストされている場合。  
  
6.  **サーバーにログオン**グループで、 **Windows 認証を使用**します。  
  
    > [!IMPORTANT]  
    >  Windows 認証は SQL Server 認証よりも安全性に優れているので、実装時はできる限り Windows 認証を使用してください。 SQL Server 認証は旧バージョンとの互換性を維持するために提供されています。 認証方法の詳細については、次を参照してください。[データベース エンジンの構成 - アカウントのプロビジョニング](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)します。  
  
7.  **を選択するか、データベース名を入力**一覧で、選択[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]順にクリックします**OK**します。  
  
8.  **[次へ]** をクリックします。  
  
9. **権限借用情報**] ページで [**サービス アカウントを使用して、**、順にクリックします **[次へ]** します。  
  
     **ウィザードの完了** ページで、既定では、データ ソースがという名前の Adventure Works DW 2012 に注意してください。  
  
10. **[完了]** をクリックします。  
  
     新しいデータ ソース、Adventure Works DW 2012 が表示されます、**データソース**ソリューション エクスプ ローラーでフォルダー。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [ソース ビューのデータの作成&#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [サービス プロジェクトの作成、分析&#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データ ソースの作成 &#40;SSAS 多次元&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)   
 [データ ソースの定義](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [権限借用オプションを設定&#40;SSAS - 多次元&#41;](../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)  
  
  

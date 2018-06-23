---
title: データ ソース (基本的なデータ マイニング チュートリアル) を作成する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b86c10563ffae3073b92373eec5e07c18c1c0668
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312590"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a>データ ソースの作成 (基本的なデータ マイニング チュートリアル)
  A*データソース*が保存されていると、プロジェクトの管理に配置されたデータ接続、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベース。 データ ソースには、ソース データが存在するサーバーとデータベースの名前、および接続に必要なその他のプロパティが含まれます。  
  
> [!IMPORTANT]  
>  データベースの名前は [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] です。 このデータベースをまだインストールがいない場合は、次を参照してください。、 [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417)ページ。  
  
### <a name="to-create-a-data-source"></a>データ ソースを作成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、**データソース**フォルダーを選択**新しいデータ ソース**です。  
  
2.  **データ ソース ウィザードへようこそ** ページで、をクリックして**次**です。  
  
3.  **接続の定義方法を選択します**] ページで [**新規**への接続を追加する、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベース。  
  
4.  **プロバイダー**一覧に**接続マネージャー****ネイティブ OLE db \sql Server Native Client 11.0**です。  
  
5.  **サーバー名**ボックスで、入力するか、インストールされているサーバーの名前を選択[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]です。  
  
     たとえば、入力**localhost**データベースがローカル サーバーでホストされている場合。  
  
6.  **サーバー ログオン**グループで、 **Windows 認証を使用する**です。  
  
    > [!IMPORTANT]  
    >  Windows 認証は SQL Server 認証よりも安全性に優れているので、実装時はできる限り Windows 認証を使用してください。 SQL Server 認証は旧バージョンとの互換性を維持するために提供されています。 認証方法の詳細については、次を参照してください。[データベース エンジンの構成 - アカウントのプロビジョニング](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)です。  
  
7.  **を選択するか、データベースの名前を入力**一覧で、選択[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] をクリックし、 **OK**です。  
  
8.  **[次へ]** をクリックします。  
  
9. **権限借用情報** ページで、をクリックして**サービス アカウントを使用**、順にクリック**次**です。  
  
     **ウィザードの完了** ページで、既定では、データ ソースは、という名前の Adventure Works DW 2012 に注意してください。  
  
10. **[完了]** をクリックします。  
  
     次のように新しいデータ ソース Adventure Works DW 2012 が表示されます、**データソース**ソリューション エクスプ ローラーでフォルダーです。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [ソース ビューのデータの作成&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [サービス プロジェクトの分析を作成する&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データ ソースの作成 &#40;SSAS 多次元&#41;](../analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional.md)   
 [データ ソースを定義します。](../analysis-services/lesson-1-2-defining-a-data-source.md)   
 [権限借用オプションを設定&#40;SSAS - 多次元&#41;](../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md)  
  
  
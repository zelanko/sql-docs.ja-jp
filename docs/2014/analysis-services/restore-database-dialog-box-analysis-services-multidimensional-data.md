---
title: データベースの復元 ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 20c836a9f18184dc6c5db59cd76358e6c4613d81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085773"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a>[データベースの復元] ダイアログ ボックス (Analysis Services - 多次元データ)
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の **[データベースの復元]** ダイアログ ボックスでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] バックアップ ファイル (.abf) 形式を使用するバックアップ ファイルから [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元できます。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
 **データベースの復元 ダイアログ ボックスを表示するには**  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[復元]** をクリックします。  
  
 **[データベースの復元]** ダイアログ ボックスには、次のページがあります。  
  
## <a name="pages"></a>ページ  
 **全般**  
 このページを使用して、復元するデータベース、データベースの復元元となるバックアップ ファイル、およびデータベースの復元時に使用する全般オプションとパスワードを選択します。 このページの詳細については、「[[全般] &#40;[データベースの復元] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **パーティション**  
 このページを使用して、ローカル パーティションを指定された場所へ復元したり、リモート パーティションをリモート バックアップ ファイルから復元したりします。 このページの詳細については、「[[パーティション] &#40;[データベースの復元] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Analysis Services データベースのバックアップと復元](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
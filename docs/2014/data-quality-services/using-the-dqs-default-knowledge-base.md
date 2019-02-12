---
title: DQS の既定のナレッジ ベースの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 40a69447a0aff678cfd53a75603200b467a542c7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016313"
---
# <a name="using-the-dqs-default-knowledge-base"></a>DQS の既定のナレッジ ベースの使用
  このトピックでは、 **(DQS) にインストールされている既定のナレッジ ベース、** DQS データ [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] について説明します。 これは、次のドメインを含む、あらかじめ構築された既定のナレッジ ベースです。  
  
-   **国/地域**:通常の長い (国/地域が指定した公式名) と短縮名 (一覧やマップなどで使用される一般的な名前)、2 文字の省略形、3 文字の省略形、および各地域の 3 桁のコードが含まれています。  先頭の値は長い名前に設定されます。  
  
-   **国/地域 (3 文字が先頭)**:通常の長い (国/地域が指定した公式名) と短縮名 (一覧やマップ、およびなどで使用される一般的な名前)、2 文字の省略形、3 文字の省略形、および各地域の 3 桁のコードが含まれています。  先頭の値は、3 文字の省略形に設定されます。  
  
-   **国/地域 (2 文字が先頭)**:通常の長い (国/地域が指定した公式名) と短縮名 (一覧やマップなどで使用される一般的な名前)、2 文字の省略形、3 文字の省略形、および各地域の 3 桁のコードが含まれています。  先頭の値は、2 文字の省略形に設定されます。  
  
-   **米国 - 郡**:米国の郡の一覧が含まれています。  
  
-   **米国 - Last Name**:最後の名前 (姓) が 100 のまたは複数回、国勢調査 2000年で一覧を含みます。  
  
-   **米国 - 場所-**:50 州、コロンビア、およびプエルトリコの国勢調査 2010年から抽出された場所の一覧が含まれています。  
  
-   **米国 - 州**:通常の長い (公式) を含む名前と米国では、各状態用の 2 文字の省略形。 先頭の値は通常の州名に設定されます。  
  
-   **米国 - 州 (2 文字)**:通常の長い (公式) を含む名前と米国では、各状態用の 2 文字の省略形。 先頭の値は、州名の 2 文字の省略形に設定されます。  
  
## <a name="using-the-default-knowledge-base"></a>既定のナレッジ ベースの使用  
 既定の DQS ナレッジ ベースである DQS データは、次の方法で使用します。  
  
-   既定のナレッジ ベースを使用してクレンジング データ品質プロジェクトを開始して実行します。先に DQS の新しいナレッジ ベースを作成する必要はありません。  
  
-   既定のナレッジ ベースで、ドメイン管理、ナレッジ検出、または照合ポリシーのアクティビティを実行します。 これを実行するには、 **Data Quality Client Home Screen** の [[ナレッジ ベースを開く]](../../2014/data-quality-services/data-quality-client-home-screen.md)をクリックし、 **[ナレッジ ベースを開く]** 画面の **[DQS Data]** ナレッジ ベースを選択して、 **[アクティビティの選択]** 領域で必要なアクティビティを選択します。 **[次へ]** をクリックします。  
  
-   既定のナレッジ ベースを使用して新しいナレッジ ベースを作成します。 既存のナレッジ ベースからナレッジ ベースを作成する方法については、「 [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md)」を参照してください。  
  
-   「 [Integration Services の DQS クレンジング コンポーネント](https://go.microsoft.com/fwlink/?LinkId=238830) 」および「 [Excel 用マスター データ サービス アドイン](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)」で、それを使用します。  
  
## <a name="see-also"></a>参照  
 [DQS のナレッジ ベースとドメイン](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  

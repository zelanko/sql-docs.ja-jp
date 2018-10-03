---
title: スナップショットの形式の指定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe570f8e23d933dfc1974564401069305e9a88a3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199932"
---
# <a name="specify-snapshot-format-sql-server-management-studio"></a>スナップショットの形式の指定 (SQL Server Management Studio)
  スナップショットの形式は、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-specify-snapshot-format"></a>スナップショットの形式を指定するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、**[ネイティブ SQL Server - サブスクライバーはすべて SQL Server を実行しているサーバーである必要があります]** または **[文字 - パブリッシャーまたはサブスクライバーで SQL Server が実行されていない場合は必須]** を選択します。  
  
    > [!NOTE]  
    >  このパブリケーションで [!INCLUDE[ssEW](../../../includes/ssew-md.md)] データベースまたは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースへのサブスクリプションをサポートする必要がある場合を除き、ネイティブ形式を選択することをお勧めします。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションとアーティクルのプロパティの変更](change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../initialize-a-subscription-with-a-snapshot.md)  
  
  

---
title: スナップショットの形式の指定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], formats
- snapshot replication [SQL Server], formats
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8e13b0635e750f8b6e59420fd25fe81af74eb7a0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811044"
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
  
  

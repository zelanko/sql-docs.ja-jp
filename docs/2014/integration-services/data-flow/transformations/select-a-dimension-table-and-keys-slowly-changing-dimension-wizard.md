---
title: '[ディメンション テーブルおよびキーの選択] (緩やかに変化するディメンション ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a62ab620db99e06f4e971e4bfe488f1741dd510
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176437"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>[ディメンション テーブルおよびキーの選択] (緩やかに変化するディメンション ウィザード)
  **[ディメンション テーブルおよびキーの選択]** ページを使用すると、読み込むディメンション テーブルを選択できます。 データ フローの列を、読み込み対象の列にマップします。  
  
 このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **Connection manager**  
 一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして OLE DB 接続マネージャーを作成します。  
  
> [!NOTE]  
>  緩やかに変化するディメンション ウィザードでは、OLE DB 接続マネージャーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続のみがサポートされます。  
  
 **[新規作成]**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して既存の接続マネージャを選択するか、 **[新規作成]** をクリックして新しい OLE DB 接続を作成します。  
  
 **[テーブルまたはビュー]**  
 一覧からテーブルまたはビューを選択します。  
  
 **[入力列]**  
 マッピングを指定する入力列を一覧から選択します。  
  
 **[ディメンション列]**  
 使用できるすべてのディメンション列を表示します。  
  
 **[キーの種類]**  
 ビジネス キーとして使用するディメンション列を 1 つ選択します。 ビジネス キーを必ず 1 つ指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [緩やかに変化するディメンション ウィザードを使用して出力を構成する](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
---
title: '[新しいデータベース] ダイアログボックス (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.newdatabase.f1
ms.assetid: ddc7804b-acb0-4ae4-a88f-e8cdf704c341
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07eeee6136965671b000923dc3f240de06ce0bd0
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541194"
---
# <a name="new-database-dialog-box-analysis-services"></a>[新しいデータベース] ダイアログ ボックス (Analysis Services)
  **の** [新しいデータベース] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、新しい空の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを作成できます。 **[新しいデータベース]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダーを右クリックし、 **[新しいデータベース]** をクリックします。  
  
## <a name="options"></a>オプション  
  
|期間|定義|  
|----------|----------------|  
|**データベース名**|新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの名前を入力します。|  
|**[特定のユーザー名とパスワードを使用する]**|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに、指定されたユーザー アカウントのセキュリティ資格情報を使用します。 処理、ROLAP クエリ、不一致バインド、ローカル キューブ、マイニング モデル、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、指定した資格情報が使用されます。 ただし DMX OPENQUERY ステートメントの場合は、現在のユーザーの資格情報が使用されます。|  
|**ユーザー名**|選択した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースによって使用されるユーザー アカウントのドメインと名前を入力します。 次の形式を使用します。<br /><br /> *\<Domain name>* **\\** *\<User account name>*<br /><br /> 注: このオプションは、 **[特定のユーザー名とパスワードを使用する]** が選択されている場合にのみ有効です。|  
|**パスワード**|**[ユーザー名]** に指定したユーザー アカウントのパスワードを入力します。|  
|**[サービス アカウントを使用する]**|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに、データベースを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サービスに関連付けられた、セキュリティ資格情報を使用します。 処理、ROLAP クエリ、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、サービス アカウント資格情報が使用されます。 DMX OPENQUERY ステートメントの場合は、ローカル キューブとマイニング モデルに現在のユーザーの資格情報が使用されます。 不一致バインドに対しては、このオプションはサポートされません。|  
|**[現在のユーザーの資格情報を使用する]**|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに、不一致バインド、DMX OPENQUERY ステートメント、ローカル キューブ、マイニング モデルに現在のユーザーのセキュリティ資格情報を使用します。 処理、ROLAP クエリ、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に対しては、このオプションはサポートされません。|  
|**[Default]**|このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]に既定のユーザー アカウントの資格情報が使用されます。 このオプションでは、オブジェクトの処理、サーバーの同期、 **OpenQuery** データ マイニング ステートメントの実行に、データベースの既定の設定が使用されます。 データベース レベルでの既定設定の指定に関する詳細については、「[多次元データベースのプロパティ設定 &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md)」をご覧ください。<br /><br /> 既定で `DataSourceImpersonationInfo` は、データベースプロパティは、**サービスアカウントを使用**するように設定されています。 `DataSourceImpersonationInfo` プロパティの値に関係なく、不一致バインド、ROLAP クエリ、ローカル キューブ、データ マイニング モデルには現在のユーザーの資格情報が使用されます。|  
|**説明**|新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースの説明を入力します。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [多次元モデル データベース &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  

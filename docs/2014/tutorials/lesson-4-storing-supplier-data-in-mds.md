---
title: 'レッスン 4: MDS に仕入先データを格納する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 678a7d6ce075e6a1082856aa7962bb3f6eec522d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489718"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>レッスン 4: MDS に仕入先データを格納する
  マスター データ サービス (MDS) は、マスター データ管理用の SQL Server ソリューションです。 マスター データ管理 (MDM) とは、データの非トランザクション リストを探索および定義するために組織が必要とする作業を表します。  
  
 モデルはマスター データ サービス内の最上位レベルの編成単位で、マスター データの構造を整理します。 MDS を実装すると、1 つ以上のモデルを作成することができ、各モデルで類似データがグループ化されます。 マスター データは通常、4 つのカテゴリ (人、場所、物、概念) のうちの 1 つに分類されます。 たとえば、製品関連のデータを含む Product モデルや、顧客関連のデータを含む Customer モデルを作成できます。 詳細については、「[モデル (マスターデータサービス)](https://msdn.microsoft.com/library/ee633746.aspx) 」を参照してください。  
  
 モデルには 1 つ以上のエンティティを含めることができます。 各エンティティには属性 (列) とメンバー (行) があります。 各行にはマスター データが含まれます。 このレッスンでは、Supplier および State という 2 つのエンティティを持つ Suppliers モデルを作成します。 Supplier エンティティには、Code、Name、Contact First Name、Contact Last Name、Contact Email Address、Address Line、City、State、Zip、および Country の属性があります。 一般的な属性の詳細については、「[属性 (マスターデータサービス)](https://msdn.microsoft.com/library/ee633745.aspx) 」を参照してください。 Code および Name 属性は、Cleansed and Matched Suppliers Excel ファイルの SupplierID および Supplier Name 列に対応します。  
  
 ドメイン ベースの属性とは、別のエンティティからのメンバーによって値が設定される属性です。 ドメイン ベースの属性では、ユーザーは有効でない属性値を入力できません。 属性値は、別のエンティティによって設定されるドロップダウン リストからのみ選択できます。 このチュートリアルでは、Supplier エンティティの State 属性は State エンティティからの値を含むドメイン ベースの属性です。 Supplier エンティティの State 属性の値は、State エンティティのいずれかの値にのみ変更できます。 詳細については[、「ドメインベースの属性](../master-data-services/domain-based-attributes-master-data-services.md)」を参照してください。  
  
 MDS 内の派生階層は、モデル内に存在するドメイン ベースの属性のリレーションシップにから派生します。 このチュートリアルでは、Supplier エンティティと State エンティティ間の派生階層を作成します。 派生階層を作成すると、マスター データ マネージャーのブラウザーに状態の一覧が表示されます。 一覧から状態をクリックすると、選択した状態の仕入先が右ペインに表示されます。 このリレーションシップに基づいて派生階層を後で作成します。 詳細については、「[派生階層](../master-data-services/derived-hierarchies-master-data-services.md)」を参照してください。  
  
 DQS でナレッジ ベースを作成し、仕入先データのクレンジングと照合に使用して、結果を Cleansed and Matched Supplier Data.xls ファイルに保存しました。 このレッスンでは、クレンジングおよび照合済みのデータを MDS にアップロードします。 DQS にはデータ (メタデータ) に関するナレッジだけが含まれ、MDS はデータ自体 (マスター セット) を保存します。 たとえば、DQS に複数の仕入先に関するナレッジが含まれている場合でも、MDS は会社が使用する仕入先のみを管理します。  
  
 このレッスンでは、次のタスクを行います。  
  
1.  **マスターデータマネージャー Web アプリケーション**を使用して、 **MDS**で**サプライヤー**モデルを作成します。  
  
2.  クレンジングされ、一致した**Supplier Data .xls**を Excel で開き、 **Excel 用 MDS アドイン**を使用して**supplier**という名前のエンティティを作成し、データを MDS にアップロードします。  
  
3.  **マスターデータマネージャー**を使用して、データが MDS で作成されていることを確認します。  
  
4.  **State という名前**のエンティティを作成し、 **state**エンティティに応じて、 **Supplier**エンティティの**state**属性をドメインベースの属性に更新します。 これを行うには、 **Excel 用 MDS アドイン**を使用します。  
  
5.  **マスターデータマネージャー**を使用してドメインベースの属性が作成されていることを確認し、 **State**エンティティの**Name**属性の値を更新します。  
  
6.  **Excel**で**マスターデータマネージャー**を使用して行った更新を表示します。  
  
7.  **State**エンティティから**Excel**に値を読み込み、値を追加して、**マスターデータマネージャー**を使用して加算を確認します。  
  
8.  派生階層を作成して使用するには、 **supplier**エンティティと**state**エンティティの間のドメインベースの属性リレーションシップを使用します (supplier エンティティの state 属性は state エンティティ型です)。そのためには、**マスターデータマネージャー**を使用します。  
  
## <a name="next-step"></a>次の手順  
 [タスク 1: マスター データ マネージャーを使用して Suppliers モデルを作成する](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  

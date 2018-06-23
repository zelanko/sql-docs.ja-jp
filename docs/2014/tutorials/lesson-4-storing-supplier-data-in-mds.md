---
title: 'レッスン 4: MDS に仕入先データを格納する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bacd9eaf-4d12-4f25-aec7-d785dec1b623
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 40f09aa6544bc38378e547c5b6e94dd26956a549
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174067"
---
# <a name="lesson-4-storing-supplier-data-in-mds"></a>レッスン 4: MDS に仕入先データを格納する
  マスター データ サービス (MDS) は、マスター データ管理用の SQL Server ソリューションです。 マスター データ管理 (MDM) とは、データの非トランザクション リストを探索および定義するために組織が必要とする作業を表します。  
  
 モデルはマスター データ サービス内の最上位レベルの編成単位で、マスター データの構造を整理します。 MDS を実装すると、1 つ以上のモデルを作成することができ、各モデルで類似データがグループ化されます。 マスター データは通常、4 つのカテゴリ (人、場所、物、概念) のうちの 1 つに分類されます。 たとえば、製品関連のデータを含む Product モデルや、顧客関連のデータを含む Customer モデルを作成できます。 参照してください[モデル (Master Data Services)](http://msdn.microsoft.com/library/ee633746.aspx)詳細についてはします。  
  
 モデルには 1 つ以上のエンティティを含めることができます。 各エンティティには属性 (列) とメンバー (行) があります。 各行にはマスター データが含まれます。 このレッスンでは、Supplier および State という 2 つのエンティティを持つ Suppliers モデルを作成します。 Supplier エンティティには、Code、Name、Contact First Name、Contact Last Name、Contact Email Address、Address Line、City、State、Zip、および Country の属性があります。 参照してください[属性 (マスター データ サービス)](http://msdn.microsoft.com/library/ee633745.aspx)の詳細に関する詳細情報属性一般にします。 Code および Name 属性は、Cleansed and Matched Suppliers Excel ファイルの SupplierID および Supplier Name 列に対応します。  
  
 ドメイン ベースの属性とは、別のエンティティからのメンバーによって値が設定される属性です。 ドメイン ベースの属性では、ユーザーは有効でない属性値を入力できません。 属性値は、別のエンティティによって設定されるドロップダウン リストからのみ選択できます。 このチュートリアルでは、Supplier エンティティの State 属性は State エンティティからの値を含むドメイン ベースの属性です。 Supplier エンティティの State 属性の値は、State エンティティのいずれかの値にのみ変更できます。 参照してください[ドメイン ベース属性](http://msdn.microsoft.com/library/ff487058.aspx)詳細についてはします。  
  
 MDS 内の派生階層は、モデル内に存在するドメイン ベースの属性のリレーションシップにから派生します。 このチュートリアルでは、Supplier エンティティと State エンティティ間の派生階層を作成します。 派生階層を作成すると、マスター データ マネージャーのブラウザーに状態の一覧が表示されます。 一覧から状態をクリックすると、選択した状態の仕入先が右ペインに表示されます。 このリレーションシップに基づいて派生階層を後で作成します。 参照してください[派生階層](http://msdn.microsoft.com/library/ee633747.aspx)詳細についてはします。  
  
 DQS でナレッジ ベースを作成し、仕入先データのクレンジングと照合に使用して、結果を Cleansed and Matched Supplier Data.xls ファイルに保存しました。 このレッスンでは、クレンジングおよび照合済みのデータを MDS にアップロードします。 DQS にはデータ (メタデータ) に関するナレッジだけが含まれ、MDS はデータ自体 (マスター セット) を保存します。 たとえば、DQS に複数の仕入先に関するナレッジが含まれている場合でも、MDS は会社が使用する仕入先のみを管理します。  
  
 このレッスンでは、次のタスクを行います。  
  
1.  作成、 **Suppliers**中のモデル**MDS**を使用して、**マスター データ マネージャー Web アプリケーション**です。  
  
2.  開いている**Cleansed and Matched Supplier Data.xls** in Excel および使用する、 **MDS アドインを Excel 用**という名前のエンティティを作成する**業者**し、データを MDS にアップロードします。  
  
3.  使用して、データが MDS で作成されたことを確認してください、**マスター データ マネージャー**です。  
  
4.  という名前のエンティティを作成する**状態**し、更新、**状態**の属性**業者**エンティティをに応じてドメイン ベースの属性を指定する、 **の状態**エンティティです。 このすべてを使用して操作を行う、 **MDS アドインを Excel 用**です。  
  
5.  使用してドメイン ベースの属性が作成されたことを確認**マスター データ マネージャー**の値を更新し、**名前**の属性、**状態**エンティティです。  
  
6.  使用して行った更新を表示**マスター データ マネージャー**で**Excel**です。  
  
7.  値を読み込み、**状態**にエンティティ**Excel** 、値を追加しを使用して、追加を確認し、**マスター データ マネージャー**です。  
  
8.  作成し、ドメイン ベースの属性リレーションシップを使用して派生階層を使用して、**業者**エンティティと**状態**(Supplier エンティティの State 属性がエンティティ型は State エンティティの) を使用して**マスター データ マネージャー**です。  
  
## <a name="next-step"></a>次の手順  
 [タスク 1: マスター データ マネージャーを使用して Suppliers モデルを作成する](../../2014/tutorials/task-1-creating-suppliers-model-using-master-data-manager.md)  
  
  
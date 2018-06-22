---
title: Microsoft Excel 用マスター データ サービス アドイン | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 06f20a19801b43a25f3622424aa8ce76d2c34df2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083007"
---
# <a name="master-data-services-add-in-for-microsoft-excel"></a>Microsoft Excel 用マスター データ サービス アドイン
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]、参照データのマスター リストは、Excel を使用して、組織内にあるすべてのユーザーに配布できます。 セキュリティによって、ユーザーが表示および更新できるデータを決定します。  
  
 フィルター処理したデータ リストを MDS から Excel に読み込んで、そのデータを他のデータと同様に Excel で操作することができます。 完了したら、データをパブリッシュして一元的な格納場所の MDS に戻すことができます。  
  
 管理者の場合は、 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] を使用してエンティティおよび属性を作成し、それらにデータを読み込みます。 これにより、他のツールを使用してデータをモデルに読み込む必要がなくなります。  
  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、Data Quality Services (DQS) を使用して、MDS に読み込む前にデータを照合できます。 これにより、MDS 内のデータの重複を防ぐことができます。  
  
> [!IMPORTANT]  
>  使用し続けることができます、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]のマスター データ サービス アドインを Excel 用マスター データ サービスと Data Quality Services をアップグレードした後の SP1 バージョン[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]CTP2 です。 ただし、SQL Server 2014 CTP2 にアップグレードした後、以前のバージョンの Excel 用マスター データ サービス アドインは機能しません。 ダウンロードすることができます、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 バージョンのマスター データ サービス アドインを使用して Excel の[ここ](http://go.microsoft.com/fwlink/?LinkId=328664)です。  
  
## <a name="terms"></a>用語  
 アドインを使用するときに、次の用語を目にすることがあります。  
  
-   *MDS repository* : すべてのマスター データが格納されている場所。 MDS データを格納するように構成されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースです。 リポジトリのデータを操作するには、そのデータを Excel に読み込みます。操作が完了したら、変更をパブリッシュしてリポジトリに戻します。 管理者は、新しいエンティティと属性をリポジトリに追加できます。  
  
-   *"MDS によって管理されるデータ"* は、MDS リポジトリに格納されているデータです。Excel に読み込むと、このデータ行は強調表示されます。 MDS によって管理されないデータをワークシートに追加できます。このようなデータは、MDS によって管理されるデータの更新時に影響を受けません。  
  
-   *model* : データのコンテナー。 複数のバージョンのコンテナーを作成することができ、通常は最後のバージョンが最新になります。 詳細については、「[モデル (マスター データ サービス)](../models-master-data-services.md)」を参照してください。  
  
-   *entity* : データのリスト。 エンティティは、データベースのテーブルと考えることができます。 たとえば、 **Color** エンティティには色のリストが含まれます。 詳細については、「[エンティティ (マスター データ サービス)](../entities-master-data-services.md)」を参照してください。  
  
-   *member* : データの行。 各エンティティにはメンバーが含まれます。 たとえば、メンバーは **Blue**などです。 詳細については、「[バージョン (マスター データ サービス)](../members-master-data-services.md)」を参照してください。  
  
-   *attribute* : データの列。 各メンバーには属性が含まれます。 たとえば、**Blue** メンバーの **Code** 属性は **B** です。属性の詳細については、「[属性 (マスター データ サービス)](../attributes-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] リポジトリへの接続を作成します。|[MDS リポジトリへの接続 &#40;Excel 用 MDS アドイン&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|MDS によって管理されるデータを Excel に読み込みます。|[MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)|  
|現在表示されている MDS によって管理されるデータを後で開くために使用できるショートカット クエリを保存します。|[ショートカット クエリ ファイルの保存 &#40;Excel 用 MDS アドイン&#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|ショートカットを他のユーザーと共有します。|[ショートカット クエリ ファイルの電子メールでの送信 &#40;Excel 用 MDS アドイン&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|メンバーに加えられたすべての変更を表示します。|[メンバーのすべての注釈またはトランザクションの表示 &#40;Excel 用 MDS アドイン&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|新しいデータをパブリッシュする前に、重複が存在するかどうかを調べます。|[類似データの照合 &#40;MDS Excel 用 MDS アドイン&#41;](match-similar-data-mds-add-in-for-excel.md)|  
|ワークシートから MDS リポジトリにデータをパブリッシュします。|[Excel からデータを MDS にパブリッシュ&#40;MDS アドインを Excel 用&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|ワークシート内のデータを含む新しいエンティティを作成します (管理者のみ)。|[エンティティの作成 &#40;Excel 用 MDS アドイン&#41;](create-an-entity-mds-add-in-for-excel.md)|  
|制約リストとも呼ばれるドメイン ベースの属性を作成します (管理者のみ)。|[ドメイン ベースの属性の作成 &#40;Excel 用 MDS アドイン&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md)|  
|Excel 用マスター データ サービス アドインで、データの読み込みとパブリッシングのプロパティを設定します。 (管理者のみ)。|[Excel 用マスター データ サービス アドインのプロパティの設定](setting-properties-for-master-data-services-add-in-for-excel.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [接続 &#40;Excel 用 MDS アドイン&#41;](connections-mds-add-in-for-excel.md)  
  
-   [データの読み込み&#40;MDS アドインを Excel 用&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [ショートカット クエリ ファイル &#40;Excel 用 MDS アドイン&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Excel 用 MDS アドインでのデータ品質照合](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
-   [データのパブリッシュ&#40;MDS アドインを Excel 用&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
-   [モデルの構築 &#40;Excel 用 MDS アドイン&#41;](building-a-model-mds-add-in-for-excel.md)  
  
-   [セキュリティ &#40;マスター データ サービス&#41;](../security-master-data-services.md)  
  
  
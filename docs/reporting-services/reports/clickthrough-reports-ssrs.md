---
title: クリックスルー レポート (SSRS) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2273d2c0108d96478aa5f5645abcb0034f6c89e5
ms.sourcegitcommit: c7febcaff4a51a899bc775a86e764ac60aab22eb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2018
ms.locfileid: "52710783"
---
# <a name="clickthrough-reports-ssrs"></a>クリックスルー レポート (SSRS)
  クリックスルー レポートとは、メイン レポートに含まれるデータの詳細情報を提供するレポートです。 クリックスルー レポートは、メイン レポートに表示される対話型データをユーザーがクリックすると表示されます。 これらのレポートは、レポート サーバーによって自動的に生成されます。 クリックスルー レポートに表示される内容は、モデルをデザインするときに、レポート モデルのエンティティに割り当てる **DefaultDetailAttribute** プロパティと **DefaultAggregateAttribute** プロパティを設定することによって指定できます。  
  
> [!NOTE]  
>  クリックスルー レポートは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2017 の各エディションとサポートされている機能](~/sql-server/editions-and-components-of-sql-server-2017.md)」をご覧ください。 組織で実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションが不明な場合は、データベース管理者に問い合わせてください。  
  
## <a name="using-default-templates"></a>既定のテンプレートの使用  
 既定では、単一インスタンス テンプレートと複数インスタンス テンプレートという 2 種類のクリックスルー テンプレートが、レポート サーバーによって各エンティティに対して生成されます。 どちらのテンプレートが使用されるかは、クリックするアイテムによって決まります。 レポートを表示しているユーザーがスカラー属性をクリックした場合は、単一インスタンス テンプレートが使用されます。 レポートを表示しているユーザーが集計属性をクリックした場合は、複数インスタンス テンプレートが使用されます。  
  
#### <a name="single-instance-templates"></a>単一インスタンス テンプレート  
 単一インスタンス テンプレートは、対象エンティティのすべての属性と、対象エンティティからの一対多のリレーションシップを持つ関連エンティティに対して指定されているすべての既定の集計属性を表示します。 単一インスタンス テンプレートは次の画像のようになります。  
  
 ![多対一のクリックスルー レポート。](../../reporting-services/reports/media/manytooneclickthrough.gif "多対一のクリックスルー レポート。")  
  
#### <a name="multiple-instance-templates"></a>複数インスタンス テンプレート  
 複数インスタンス テンプレートは、対象エンティティの既定の詳細属性のみと、対象エンティティからの一対多のリレーションシップを持つ関連エンティティに対して指定されているすべての既定の集計属性を表示します。 複数インスタンス テンプレートは次の画像のようになります。  
  
 ![多対一のクリックスルー レポート。](../../reporting-services/reports/media/onetomanyclickthrough.gif "多対一のクリックスルー レポート。")  
  
## <a name="customizing-clickthrough-reports"></a>クリックスルー レポートのカスタマイズ  
 レポート サーバーによって生成される既定のテンプレートを使用する代わりに、レポート ビルダーでレポートを作成して、カスタマイズしたクリックスルー レポートとして使用することができます。 次に、レポートを、レポート マネージャーの詳細レポートとしてモデルにリンクできます。  
  
 レポート ビルダーのレポートをクリックスルー レポートにするには、レポート ビルダーの **[プロパティ]** ダイアログ ボックスの **[ドリルスルーを有効にする]** オプションをクリックする必要があります。 このオプションをクリックすると、レポートにドリルスルー パラメーターが追加されて、レポートを直接レポート ビルダーで実行できなくなります。 ドリルスルー パラメーターは、レポートを表示しているユーザーがレポート ビルダーのレポートの中のアイテムをクリックしたときに、レポート サーバーによって自動的に計算されます。  
  
> [!IMPORTANT]  
>  レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。  
  
## <a name="see-also"></a>参照  
 [レポートをクリックスルー レポートとしてモデルにリンクする](https://msdn.microsoft.com/library/3af42de3-67ef-41c2-bc8a-7045baec6f63)  
  
  

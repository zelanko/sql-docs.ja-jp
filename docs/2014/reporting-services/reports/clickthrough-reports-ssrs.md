---
title: クリックスルー レポート (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
caps.latest.revision: 28
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: c6bb00e29b5edc039d33a345addc596f18669f3e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177236"
---
# <a name="clickthrough-reports-ssrs"></a>クリックスルー レポート (SSRS)
  クリックスルー レポートとは、メイン レポートに含まれるデータの詳細情報を提供するレポートです。 クリックスルー レポートは、メイン レポートに表示される対話型データをユーザーがクリックすると表示されます。 これらのレポートは、レポート サーバーによって自動的に生成されます。 モデル デザイナーでは、判断を設定して、クリックスルー レポートに表示される内容、`DefaultDetailAttribute`と`DefaultAggregateAttribute`レポート モデル内のエンティティに割り当てられるプロパティ。  
  
> [!NOTE]  
>  クリックスルー レポートでは使用できませんのすべてのエディション[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 各エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[SQL Server 2014 のエディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。 組織で実行している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のエディションが不明な場合は、データベース管理者に問い合わせてください。  
  
## <a name="using-default-templates"></a>既定のテンプレートの使用  
 既定では、単一インスタンス テンプレートと複数インスタンス テンプレートという 2 種類のクリックスルー テンプレートが、レポート サーバーによって各エンティティに対して生成されます。 どちらのテンプレートが使用されるかは、クリックするアイテムによって決まります。 レポートを表示しているユーザーがスカラー属性をクリックした場合は、単一インスタンス テンプレートが使用されます。 レポートを表示しているユーザーが集計属性をクリックした場合は、複数インスタンス テンプレートが使用されます。  
  
#### <a name="single-instance-templates"></a>単一インスタンス テンプレート  
 単一インスタンス テンプレートは、対象エンティティのすべての属性と、対象エンティティからの一対多のリレーションシップを持つ関連エンティティに対して指定されているすべての既定の集計属性を表示します。 単一インスタンス テンプレートは次の画像のようになります。  
  
 ![多対一のクリックスルー レポート。](../media/manytooneclickthrough.gif "多対一のクリックスルー レポート。")  
  
#### <a name="multiple-instance-templates"></a>複数インスタンス テンプレート  
 複数インスタンス テンプレートは、対象エンティティの既定の詳細属性のみと、対象エンティティからの一対多のリレーションシップを持つ関連エンティティに対して指定されているすべての既定の集計属性を表示します。 複数インスタンス テンプレートは次の画像のようになります。  
  
 ![多対一のクリックスルー レポート。](../media/onetomanyclickthrough.gif "多対一のクリックスルー レポート。")  
  
## <a name="customizing-clickthrough-reports"></a>クリックスルー レポートのカスタマイズ  
 レポート サーバーによって生成される既定のテンプレートを使用する代わりに、レポート ビルダーでレポートを作成して、カスタマイズしたクリックスルー レポートとして使用することができます。 次に、レポートを、レポート マネージャーの詳細レポートとしてモデルにリンクできます。  
  
 レポート ビルダーのレポートをクリックスルー レポートにするには、レポート ビルダーの **[プロパティ]** ダイアログ ボックスの **[ドリルスルーを有効にする]** オプションをクリックする必要があります。 このオプションをクリックすると、レポートにドリルスルー パラメーターが追加されて、レポートを直接レポート ビルダーで実行できなくなります。 ドリルスルー パラメーターは、レポートを表示しているユーザーがレポート ビルダーのレポートの中のアイテムをクリックしたときに、レポート サーバーによって自動的に計算されます。  
  
> [!IMPORTANT]  
>  レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。  
  
## <a name="see-also"></a>参照  
 [レポートをクリックスルー レポートとしてモデルにリンクする](../link-a-report-to-a-model-as-a-clickthrough-report.md)  
  
  
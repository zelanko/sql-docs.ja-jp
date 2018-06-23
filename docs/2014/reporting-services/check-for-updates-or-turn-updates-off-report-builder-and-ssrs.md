---
title: 更新プログラムまたは更新をオフ (レポート ビルダーおよび SSRS) のチェック |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: c355099f67128f90a958d59f91de5f0d21c68a19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165195"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a>更新を確認するまたは更新をオフにする (レポート ビルダーおよび SSRS)
  レポートを開くたびに、レポート ビルダーによって、そのレポートにあるレポート パーツのパブリッシュ済みインスタンスがレポート サーバー、またはレポート サーバーと統合されている SharePoint サイト上で更新されたかどうかが確認されます。 また、データセットやパラメーターなどのレポート パーツの依存アイテムに変更が加えられたかどうかも確認されます。 レポート パーツまたはレポート パーツの依存アイテムがサイトまたはサーバー上で更新されている場合は、レポート内の情報バーに、更新されたパーツの数が表示されます。 更新は、表示して受け入れることも、拒否することもできます。また、情報バーを消去することもできます。  
  
 情報バーを無効にして、レポート パーツのパブリッシュ済みインスタンスの変更に関する情報が表示されないようにすることもできます。 これは、そのユーザーが開くすべてのレポートでこの機能を無効にするためのユーザー設定です。 情報バーを無効にした場合でも、更新を確認できます。  
  
### <a name="to-turn-on-and-off-report-part-updates"></a>レポート パーツ更新のオン/オフを切り替えるには  
  
1.  レポート ビルダーのボタンをクリックし、をクリックして**オプション**です。  
  
2.  **オプション**ダイアログ ボックスの**リソース** タブ、オンまたはオフ、**個人用レポートのレポート パーツに対する更新プログラムを表示**チェック ボックスをオンします。  
  
> [!NOTE]  
>  これは、ユーザー設定です。 そのユーザーが開くすべてのレポートで無効になります。  
  
### <a name="to-check-for-updates"></a>更新を確認するには  
  
-   レポートの外側またはレポート本文には、デザイン サーフェイスを右クリックし、をクリックして**更新プログラムを確認**です。  
  
## <a name="see-also"></a>参照  
 [レポート パーツ&#40;レポート ビルダーおよび SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [およびレポート パーツを再パブリッシュ&#40;レポート ビルダーおよび SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md)   
 [レポート パーツの参照し、既定のフォルダーを設定&#40;レポート ビルダーおよび SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)   
 [レポート パーツのトラブルシューティング&#40;レポート ビルダーおよび SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [レポート ビルダーのレポート パーツおよびデータセット](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
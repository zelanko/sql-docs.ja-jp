---
title: アタッチし、Analysis Services データベースをデタッチ |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 55d490d5fa8ca9dadeacdf9b5fd9e77c3edcb057
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attach-and-detach-analysis-services-databases"></a>Analysis Services データベースのインポートとデタッチ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者 (DBA) がデータベースを一時的にオフラインにした後、そのデータベースを同じサーバー インスタンスまたは別のサーバー インスタンス上でオンラインに戻すことは少なくありません。 こうした状況は、パフォーマンス向上のためにデータベースを別のディスクに移動したり、データベース拡張のための領域を確保したり、製品をアップグレードしたりするなど、ビジネス上のニーズによって頻繁に発生します。 このような状況だけでなくさまざまな場合に、 **Attach** コマンドと **Detach** コマンドを使用することによって、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の DBA は、データベースをオフラインにした後、簡単にオンラインに戻すことができます。  
  
## <a name="attach-and-detach-commands"></a>Attach コマンドと Detach コマンド  
 **Attach** コマンドを使用すると、オフラインになっているデータベースをオンラインにすることができます。 データベースは元のサーバー インスタンスにでも、別のインスタンスにでもアタッチできます。 データベースをアタッチする場合、データベースに **ReadWriteMode** 設定を指定できます。 **Detach** コマンドを使用すると、データベースをサーバーからオフラインにすることができます。  
  
## <a name="attach-and-detach-usage"></a>Attach と Detach の使用方法  
 **Attach** コマンドは、既存のデータベース構造をオンラインにする際に使用します。 データベースを **ReadWrite** モードでアタッチする場合は、1 つのサーバー インスタンスに 1 回だけアタッチできます。 一方、データベースを **ReadOnly** モードでアタッチする場合は、異なるサーバー インスタンスに複数回アタッチできます。 ただし、同じデータベースを同じサーバー インスタンスに複数回アタッチすることはできません。 同じデータベースを複数回アタッチしようとすると、データを別のフォルダーにコピーした場合でも、エラーが発生します。  
  
> [!IMPORTANT]  
>  データベースをデタッチする際にパスワードが必要だった場合は、そのデータベースをアタッチする際にも同じパスワードが必要になります。  
  
 **Detach** コマンドは、既存のデータベース構造をオフラインにする際に使用します。 データベースをデタッチする場合は、パスワードを指定して、機密性のあるメタデータを保護する必要があります。  
  
> [!IMPORTANT]  
>  データ ファイルの内容を保護するには、フォルダー、サブフォルダー、およびデータ ファイルのアクセス制御リストを使用する必要があります。  
  
 データベースをデタッチする場合、サーバーでは次の手順を実行します。  
  
|読み書き可能なデータベースのデタッチ|読み取り専用データベースのデタッチ|  
|--------------------------------------|-------------------------------------|  
|1) サーバーはデータベースに対する CommitExclusive ロックの要求を発行します<br /><br /> 2) サーバーは、実行中のトランザクションすべてがコミットまたはロールバックされるまで待機します<br /><br /> 3) サーバーはデータベースのデタッチに必要なすべてのメタデータを構築します<br /><br /> 4) データベースは削除済みに設定されます<br /><br /> 5) サーバーはトランザクションをコミットします|1) データベースは削除済みに設定されます<br /><br /> 2) サーバーはトランザクションをコミットします<br /><br /> 注: 読み取り専用データベースでは、デタッチ用のパスワードを変更できません。 アタッチされたデータベースに既にパスワードが含まれている場合にパスワード パラメーターを指定すると、エラーが発生します。|  
  
 **Attach** コマンドおよび **Detach** コマンドは 1 つの操作として実行する必要があります。 同じトランザクション内でその他の操作と組み合わせることはできません。 また、 **Attach** コマンドおよび **Detach** コマンドはアトミックなトランザクション コマンドです。 つまり、操作は成功するか失敗するかのどちらかになります。 データベースは未完了の状態にしておくことはできません。  
  
> [!IMPORTANT]  
>  **Detach** コマンドを実行するには、サーバーまたはデータベースの管理者特権が必要です。  
  
> [!IMPORTANT]  
>  **Attach** コマンドを実行するには、サーバーの管理者特権が必要です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Analysis Services データベースを移動します。](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)   
 [Detach 要素](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Attach 要素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)  
  
  

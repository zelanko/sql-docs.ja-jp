---
title: エクスポートし、インポートのデータ マイニング オブジェクト |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9285699bf57637327bc56368a87680f20de81f23
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177622"
---
# <a name="export-and-import-data-mining-objects"></a>データ マイニング オブジェクトのエクスポートおよびインポート
  SQL Server データ マイニングでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されている、ソリューションをバックアップ、復元、および移行するための機能に加えて、データ マイニング拡張機能 (DMX) を使用して異なるサーバー間でデータ マイニング構造およびデータ マイニング モデルをすばやく転送する機能を提供しています。  
  
 データ マイニング ソリューションでは、多次元データベースではなくリレーショナル データを使用している場合を使用してモデルを転送する`EXPORT`と`IMPORT`方がすばやくデータベースの復元を使用するか、ソリューション全体を展開するよりも簡単です。  
  
 このセクションでは、DMX ステートメントを使用してデータ マイニング構造およびデータ マイニング モデルを転送する方法の概要について説明します。 構文の詳細と例については、「[EXPORT (DMX)](/sql/dmx/export-dmx)」および「[IMPORT (DMX)](/sql/dmx/import-dmx)」を参照してください。  
  
> [!NOTE]  
>  Microsoft SQL Server Analysis Services データベースからオブジェクトをエクスポートまたはインポートするには、データベースまたはサーバーの管理者である必要があります。  
  
## <a name="exporting-data-mining-structures"></a>データ マイニング構造のエクスポート  
 マイニング構造をエクスポートすると、EXPORT ステートメントによって関連するすべてのモデルが自動的にエクスポートされます。 エクスポートするオブジェクトを制御する場合は、各オブジェクトの名前を指定する必要があります。  
  
 マイニング構造が処理されて結果がキャッシュされた場合 (既定の動作) に、マイニング構造をエクスポートすると、定義には、構造の基になっているデータの概要が含まれます。 この概要を削除するを実行して、マイニング構造に関連付けられているキャッシュをクリアする必要があります、`Process Clear Structure`操作します。 詳細については、「 [マイニング構造の処理](process-a-mining-structure.md)」を参照してください。  
  
### <a name="exporting-data-mining-models"></a>データ マイニング モデルのエクスポート  
 使用することができます、`WITH DEPENDENCIES`をデータ ソースとマイニング モデルとその構造と共にデータ ソース ビューの定義をエクスポートするキーワードです。  
  
 依存関係をエクスポートせずにマイニング モデルをエクスポートすると、EXPORT ステートメントによってマイニング モデルとそのマイニング構造の定義がエクスポートされますが、データ ソースの定義はエクスポートされません。 そのため、モデルのインポート後は、直ちにモデルを参照できますが、対象サーバーでマイニング モデルを再処理する場合や、基になるデータに対してクエリを実行する場合は、エクスポート先のサーバーに、対応するデータ ソースを作成する必要があります。  
  
## <a name="importing-data-mining-structures-and-models"></a>データ マイニング構造とデータ マイニング モデルのインポート  
 データ マイニング オブジェクトをインポートする場合、IMPORT ステートメントの実行時に接続しているサーバーまたはデータベースにオブジェクトがインポートされます。 サーバー上に存在しないデータベースがインポート ファイルに含まれている場合は、そのデータベースが作成されます。  
  
 使用して、マイニング構造またはマイニング モデルをインポートすることも、`Restore`コマンド。 モデルや構造は、エクスポート元のデータベースと同じ名前のデータベースに復元されます。 詳細については、「 [復元オプション](../multidimensional-models/restore-options.md)」を参照してください。  
  
## <a name="remarks"></a>コメント  
 同じ名前のモデルや構造がインポート先のサーバーに既に存在する場合は、モデルや構造をインポートできません。 また、データ マイニング オブジェクトをエクスポートしてから、エクスポート ファイルに含まれるオブジェクトの名前を変更することもできません。 したがって、名前の競合が予想される場合は、インポート先のサーバー上のデータ マイニング オブジェクトを削除するか、定義をエクスポートする前にデータ マイニング オブジェクトの名前を変更する必要があります。  
  
## <a name="see-also"></a>参照  
 [データ マイニング ソリューションおよびオブジェクトの管理](management-of-data-mining-solutions-and-objects.md)  
  
  

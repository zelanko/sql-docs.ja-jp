---
title: データの検証 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a01af53372a8be1fce6ffa2e4ee8d4cddce8d057
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135342"
---
# <a name="validating-data-mds-add-in-for-excel"></a>データの検証 (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でデータをパブリッシュするときに、以下の 2 種類の検証が実行されます。  
  
-   定義されているすべてのビジネス ルールがデータに適用されます。  
  
-   許可されている属性値 (文字数やデータ型など) に対してデータがチェックされます。  
  
 どちらの場合も、有効なデータが MDS リポジトリにパブリッシュされます。 無効なデータは強調表示され、エラーの詳細は状態列で確認できます。  
  
## <a name="when-validation-occurs"></a>検証が実行されるタイミング  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]検証は、新しいまたは変更されたデータをパブリッシュするとき、またはビジネス ルールを手動で適用するときに発生します。  
  
 ビジネス ルールの検証に失敗しても、データは MDS リポジトリにパブリッシュされます。 入力の検証が失敗した場合は、データはリポジトリにパブリッシュされません。  
  
## <a name="validation-statuses"></a>検証状態  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で考えられる検証状態は、次のとおりです。  
  
|状態|説明|  
|------------|-----------------|  
|[エラー]|行内の 1 つ以上の値で、MDS 管理者によって定義されたビジネス ルールに対する検証が失敗しました。|  
|未検証|行内の値は、ビジネス ルールに対してまだ検証されていません。|  
|成功|行内のすべての値は、ビジネス ルールに対する検証にパスしました。|  
  
## <a name="input-statuses"></a>入力状態  
 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で考えられる入力状態は、次のとおりです。  
  
|状態|説明|  
|------------|-----------------|  
|[エラー]|行内の 1 つ以上の値が、長さやデータ型などのシステム要件を満たしていません。 MDS リポジトリ内の値は更新されません。|  
|新しい行|行内の値は、まだ MDS リポジトリにパブリッシュされていません。|  
|[読み取り専用]|ログインしているユーザーは、行内の 1 つ以上の値に対して読み取り専用の権限を持っていて、値は更新されません。|  
|変更なし|行の値は、ワークシート内で変更されていません。 これは、リポジトリ内の値が変更されていないという意味ではありません。シート内の最新のデータを取得するには、 **[接続と読み込み]** グループで、 **[読み込みまたは更新]** をクリックします。<br /><br /> これは、各行の既定の設定です。|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|定義されているビジネス ルールで失敗する値を決定します。|[ビジネス ルールの適用&#40;MDS アドインの Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)|  
|検証エラーを修正するために、メンバーに対して実行されたすべてのトランザクションを確認します。|[メンバーのすべての注釈またはトランザクションの表示 &#40;Excel 用 MDS アドイン&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [データのパブリッシュ&#40;MDS アドインの Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  

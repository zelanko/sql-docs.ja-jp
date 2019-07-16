---
title: 競合のマージ (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf95978f-a2c5-4325-8606-dbd4e88741b8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 22c25126106c6b93d779b6c494af0bff7b5b08af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68074563"
---
# <a name="merge-conflicts-mds-add-in-for-excel"></a>競合のマージ (Excel 用 MDS アドイン)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Excel 用の [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] アドインでは、サーバー上でデータが他のユーザーによって変更されている場合、パブリッシュ操作は競合エラーで失敗します。 このエラーを解決するには、競合のマージを実行した後で変更を再パブリッシュします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
-   更新するエンティティのリーフ モデル オブジェクトに対する更新権限が最低限必要です。  
  
-   アクティブなワークシートに MDS によって管理されるデータが含まれている必要があります。  
  
-   変更内容を公開しようとしたときに、アクティブなワークシートで競合エラーが発生している必要があります。  
  
### <a name="to-merge-conflicts"></a>競合をマージするには  
  
1.  ワークシートで、競合エラーが発生している行またはセルを選択します。  
  
2.  **[パブリッシュと検証]** メニュー グループの **[競合のマージ]** を選択して **[競合のマージ]** カタログを開きます。  
  
3.  **[競合のマージ]** ダイアログで、次のいずれかの操作を実行できます。  
  
    -   保留中の変更を元に戻し、サーバーから最新のバージョンを再び読み込む場合は、 **[最新]** を選択し、 **[適用]** をクリックします。  
  
    -   ワークシートの元のバージョンを適用する場合は、 **[オリジナル]** を選択し、 **[適用]** をクリックします。  
  
    -   既存のローカルの変更を保持する場合は、 **[このユーザーの変更]** を選択し、 **[適用]** をクリックします。  
  
4.  **[適用]** をクリックした後、さらに変更を加えて、再びパブリッシュすることができます。 または、 **[キャンセル]** をクリックして更新を取り消し、サーバーから最新のバージョンを再び読み込むことができます。  
  
## <a name="see-also"></a>関連項目  
 [概要:Excel からデータをインポートする&#40;MDS アドインの Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  

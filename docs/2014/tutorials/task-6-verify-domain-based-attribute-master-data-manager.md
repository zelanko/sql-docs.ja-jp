---
title: 'タスク 6: マスターデータマネージャー | を使用してドメインベースの属性が作成されていることを確認するMicrosoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: fe3f404d4f41e2977ef389216dcbc9106327266a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65488950"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a>タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する
  ここでは、**State** エンティティが **MDS** で作成されたことと、**Supplier** エンティティの **State** 属性が **State** エンティティに依存するドメイン ベースの属性であることを、**マスター データ マネージャー**を使用して確認します。  
  
1.  
  **マスター データ マネージャー** Web アプリケーションに切り替えます。  
  
2.  上部に表示されている **[SQL Server 2012 マスター データ サービス]** をクリックして、ホーム ページに移動します。  
  
3.  
  **Suppliers** モデルがオンになっていることを確認し、**[エクスプローラー]** をクリックします。 
  **エクスプローラー**が既に開いている場合は、ページを更新します。  
  
4.  メニュー バーの **[エンティティ]** にマウス カーソルを合わせます。ここで、現在、**Supplier** および **State** の 2 つのエンティティがあることに注意してください。  
  
     ![州と仕入先がある [エンティティ] メニュー](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "州と仕入先がある [エンティティ] メニュー")  
  
5.  エンティティがまだ開いていない場合は **[State]** をクリックします。  
  
6.  一覧から **[GA]** を選択します。  
  
7.  
  **[詳細]** ペインの**右ペイン**で **[名前]** を "**Georgia**" に変更し、**[OK]** をクリックします。  
  
8.  その他の州について前の手順を繰り返します。  
  
    |コード|Name|  
    |----------|----------|  
    |CA|カリフォルニア|  
    |CO|コロラド|  
    |IL|イリノイ州|  
    |DC|ワシントン D.C.|  
    |FL|フロリダ|  
    |AL|アラバマ|  
    |KY|ケンタッキー|  
    |MA|マサチューセッツ|  
    |AZ|アリゾナ|  
    |MI|ミシガン|  
    |MN|ミネソタ|  
    |NJ|ニュージャージー|  
    |NV|ネバダ|  
    |NY|ニューヨーク|  
    |OH|オハイオ|  
    |OK|オクラホマ|  
    |OR|オレゴン|  
    |PA|ペンシルベニア|  
    |SC|サウスカロライナ|  
    |KS|カンザス|  
    |TN|テネシー|  
    |TX|テキサス|  
    |UT|ユタ|  
    |VA|バージニア州|  
    |WA|ワシントン|  
    |WI|ウィスコンシン|  
    |HI|ハワイ|  
    |MD|メリーランド|  
    |CT|コネチカット|  
  
9. 州のいずれかのエントリを選択し、ツール バーの **[トランザクションの表示]** をクリックします。 先ほど行った更新に関するトランザクションが、トランザクションの一覧に表示されます。  
  
10. 
  **[エンティティ]** メニューにマウス カーソルを合わせ、**[Supplier]** をクリックします。  
  
11. ここで、**[State]** フィールドの値は、**[詳細]** ペインでドロップダウン リストを使用して変更できることに注意してください。 また、左側の一覧と **[詳細]** ペインのドロップダウン リストでは、最初に表示されたコードに続いて中かっこで囲まれた名前が表示されます。 
  **[詳細]** ペインでは、その他の値も変更できます。  
  
     ![コードと名前が更新された州の属性](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "コードと名前が更新された州の属性")  
  
## <a name="next-step"></a>次のステップ  
 [タスク 7: Excel でマスター データ マネージャーを使用して行った更新を表示する](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)  
  
  

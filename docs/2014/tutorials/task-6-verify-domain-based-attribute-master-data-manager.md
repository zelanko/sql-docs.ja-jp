---
title: 'タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性を作成することを確認します |。Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 042cff6f687bb54466afb2334ad95402de319e94
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207112"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a>タスク 6: マスター データ マネージャーを使用してドメイン ベースの属性が作成されていることを確認する
  ここでは、**State** エンティティが **MDS** で作成されたことと、**Supplier** エンティティの **State** 属性が **State** エンティティに依存するドメイン ベースの属性であることを、**マスター データ マネージャー**を使用して確認します。  
  
1.  **マスター データ マネージャー** Web アプリケーションに切り替えます。  
  
2.  上部に表示されている **[SQL Server 2012 マスター データ サービス]** をクリックして、ホーム ページに移動します。  
  
3.  **Suppliers** モデルがオンになっていることを確認し、**[エクスプローラー]** をクリックします。 **エクスプローラー**が既に開いている場合は、ページを更新します。  
  
4.  メニュー バーの **[エンティティ]** にマウス カーソルを合わせます。ここで、現在、**Supplier** および **State** の 2 つのエンティティがあることに注意してください。  
  
     ![州と仕入先にエンティティ メニュー](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "州と仕入先にエンティティ メニュー")  
  
5.  エンティティがまだ開いていない場合は **[State]** をクリックします。  
  
6.  一覧から **[GA]** を選択します。  
  
7.  **[詳細]** ペインの**右ペイン**で **[名前]** を "**Georgia**" に変更し、**[OK]** をクリックします。  
  
8.  その他の州について前の手順を繰り返します。  
  
    |コード|名前|  
    |----------|----------|  
    |CA|California|  
    |CO|Colorado|  
    |IL|Illinois|  
    |DC|District of Columbia|  
    |FL|Florida|  
    |AL|Alabama|  
    |KY|Kentucky|  
    |MA|Massachusetts|  
    |AZ|Arizona|  
    |MI|Michigan|  
    |MN|Minnesota|  
    |NJ|New Jersey|  
    |NV|Nevada|  
    |NY|New York|  
    |OH|Ohio|  
    |OK|Oklahoma|  
    |OR|Oregon|  
    |PA|Pennsylvania|  
    |SC|South Carolina|  
    |KS|Kansas|  
    |TN|Tennessee|  
    |TX|Texas|  
    |UT|Utah|  
    |VA|Virginia|  
    |WA|Washington|  
    |WI|Wisconsin|  
    |HI|Hawaii|  
    |MD|Maryland|  
    |CT|Connecticut|  
  
9. 州のいずれかのエントリを選択し、ツール バーの **[トランザクションの表示]** をクリックします。 先ほど行った更新に関するトランザクションが、トランザクションの一覧に表示されます。  
  
10. **[エンティティ]** メニューにマウス カーソルを合わせ、**[Supplier]** をクリックします。  
  
11. ここで、**[State]** フィールドの値は、**[詳細]** ペインでドロップダウン リストを使用して変更できることに注意してください。 また、左側の一覧と **[詳細]** ペインのドロップダウン リストでは、最初に表示されたコードに続いて中かっこで囲まれた名前が表示されます。 **[詳細]** ペインでは、その他の値も変更できます。  
  
     ![更新されたコードと名前を持つ属性の状態](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "更新されたコードと名前を持つ属性の状態")  
  
## <a name="next-step"></a>次の手順  
 [タスク 7: Excel でマスター データ マネージャーを使用して行った更新を表示する](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)  
  
  

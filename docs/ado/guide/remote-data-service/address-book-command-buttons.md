---
title: "アドレス帳コマンド ボタン |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 31b0bb389b188c39b4590a774ac453a9de17fd56
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="address-book-command-buttons"></a>アドレス帳コマンド ボタン
アドレス帳アプリケーションには、次のコマンド ボタンが含まれます。  
  
-   A**検索**データベースにクエリを送信するボタンをクリックします。  
  
-   A**オフ**新規検索を開始する前に、テキスト ボックスをクリアするボタンをクリックします。  
  
-   **プロファイルの更新**従業員レコードに変更を保存するボタンをクリックします。  
  
-   A**キャンセル変更**変更を破棄するボタンをクリックします。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="find-button"></a>検索 ボタン  
 クリックすると、**検索** ボタンを作成し、SQL クエリを送信する、VBScript Find_OnClick Sub プロシージャをアクティブにします。 このボタンをクリックすると、データ グリッドが表示されます。  
  
## <a name="building-the-sql-query"></a>SQL クエリの作成  
 Find_OnClick Sub プロシージャの最初の部分は、グローバル SQL SELECT ステートメントをテキスト文字列を追加することによって、SQL クエリを一度に 1 つの句を構築します。 変数を設定して開始`myQuery`データ ソース テーブルからすべての行のデータを要求するための SQL SELECT ステートメントにします。 次に、Sub プロシージャは、ページで次の 4 つの入力ボックスのそれぞれをスキャンします。  
  
 プログラムは、word を使用するため`like`SQL ステートメントの作成、クエリは完全一致ではなく、部分文字列を検索します。  
  
 などの場合、 **Last Name**  ボックスには、エントリ"Berge"が含まれていると**タイトル** ボックスには、エントリ「プログラム マネージャー」が、SQL ステートメントが含まれている (の値`myQuery`) のようになります。  
  
```  
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 クエリが成功した場合は、単語「プログラム マネージャー」(たとえば、プログラム マネージャー、高度なテクノロジ) を含むタイトルとテキスト (Berge Berger など) には、"Berge"を含む最後の名前を持つすべての担当者が HTML データ グリッドに表示されます。  
  
## <a name="preparing-and-sending-the-query"></a>準備とクエリを送信  
 Find_OnClick Sub プロシージャの最後の部分は、2 つのステートメントで構成されます。 最初のステートメントは、代入、 [SQL](../../../ado/reference/rds-api/sql-property.md)のプロパティ、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)動的に作成した SQL クエリと等しいオブジェクト。 2 番目のステートメントにより、 **.rds ですDataControl**オブジェクト (`DC1`) をデータベースを照会し、グリッドに、クエリの結果を表示します。  
  
```  
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>[プロファイル] ボタンを更新します。  
 クリックすると、**プロファイルの更新**ボタンを実行する、VBScript Update_OnClick Sub プロシージャをアクティブ化、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md)と[更新](../../../ado/reference/rds-api/refresh-method-rds.md)メソッドです。  
  
```  
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 ときに`DC1.SubmitChanges`を実行するリモートのデータ サービスは、すべての更新情報をパッケージ化し、HTTP 経由でサーバーに送信します。 更新プログラムは、0/1 です。更新プログラムの一部が失敗した場合は、どの変更を行い、ステータス メッセージが返されます。 `DC1.Refresh`後に必要はありません**SubmitChanges**をリモートのデータ サービスが新しいデータを確実にします。  
  
## <a name="cancel-changes-button"></a>[キャンセル] ボタンの変更  
 クリックすると**キャンセル変更**を実行する、VBScript Cancel_OnClick Sub プロシージャをアクティブ化、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの (`DC1)` [ただし](../../../ado/reference/rds-api/cancelupdate-method-rds.md)メソッドです。  
  
```  
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 ときに`DC1.CancelUpdate`を実行するユーザーが行ったデータ グリッドに従業員レコードを最後のクエリまたは更新されてから編集を破棄します。 元の値を復元します。  
  
## <a name="see-also"></a>参照  
 [アドレス帳のナビゲーション ボタン](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)




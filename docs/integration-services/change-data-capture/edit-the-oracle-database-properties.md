---
title: "Oracle データベースのプロパティを編集 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c310a25fe5098cd5edc845c3a29d024182f6361c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="edit-the-oracle-database-properties"></a>Oracle データベースのプロパティの編集
  プロパティ エディターの [Oracle] タブを使用して、新しいインスタンス ウィザードの [CDC データベースの作成] ページで指定した説明を変更し、Oracle ログ マイニング データベースの接続情報を変更します。  
  
 **[Oracle]** タブの情報について、次に説明します。  
  
 **名前**  
 新しいインスタンス ウィザードの [CDC データベースの作成] ページで入力した CDC インスタンスの名前です。 このフィールドは読み取り専用であり、この情報を編集することはできません。  
  
 **Description**  
 新しいインスタンスの説明を編集するか、CDC インスタンスの作成時に説明を追加しなかった場合は説明を追加できます。  
  
 **[Oracle 接続文字列]**  
 使用している Oracle データベースがあるコンピューターへの Oracle 接続文字列です。 このフィールドは読み取り専用であり、この情報を編集することはできません。 これは、接続文字列を変更すると、Oracle CDC インスタンスがまったく別の Oracle データベースを指定し、 **cdc.xdbcdc_config** テーブルに格納された CDC インスタンスの状態が破損することがあるためです。 小規模な変更が必要な場合は、SQL Server Management Studio を使用して、接続文字列を構成テーブルで直接変更できます。  
  
 **[Oracle ログ マイニング認証]**  
 ログ マイナーを含む Oracle データベースの認証資格情報を入力するには、 **[認証]**で次のいずれかを選択します。  
  
-   **[Windows 認証]**: 現在の Windows ドメイン資格情報を使用する場合に選択します。 このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。  
  
-   **[Oracle 認証]**: このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。  
  
 Oracle データベースのプロパティは、ビューアーで表示できます。 ビューアーを使用する場合、情報は読み取り専用です。 ビューアーには、テーブルのキャプチャ対象列の一覧も含まれています。 ビューアーへのアクセス方法については、「 [How to Manage a CDC Instance](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CDC デザイナー コンソールから CDC サービスを管理する方法](../../integration-services/change-data-capture/how-to-manage-a-cdc-service-from-the-cdc-designer-console.md)   
 [Oracle ソース データベースへの接続します。](../../integration-services/change-data-capture/connect-to-an-oracle-source-database.md)   
 [Oracle への接続します。](../../integration-services/change-data-capture/connect-to-oracle.md)  
  
  


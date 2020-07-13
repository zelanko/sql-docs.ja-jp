---
title: データ移行の設定 (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94d7a083-2dbc-4e3d-94dd-92b7ff9d0c2d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 9fcf6142a0df913c33782b4c65e8e95d4fcf91ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029377"
---
# <a name="data-migration-settings-sybasetosql"></a>データ移行の設定 (SybaseToSQL)
  
## <a name="data-migration-settings"></a>データの移行設定  
**データ移行設定**を使用すると、ユーザーはデータ移行のためのカスタムクエリを作成できます。  
  
-   このタブは、[プロジェクトの設定] で [**非表示**] に設定した場合に、[**拡張データ移行オプション**] が [**表示**] に設定され、非表示になるときに使用できます。 プロジェクトの移行設定の詳細については、「[プロジェクトの設定 (移行)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924) 」を参照してください。  
  
-   カスタム SQL ステートメントの解析は、テーブルノードの [**データ移行の設定**] タブで実装されます。  
  
-   **データ移行設定**可視化で使用できる2つのチェックボックスを次に示します。  
  
    1.  SQL Server テーブルの切り捨て  
  
    2.  カスタム選択の使用  
  
1.  **SQL Server テーブルの切り捨て:**  
     このオプションを使用すると、移行されたデータを対象のデータベースに明確に表示できます。  
  
    -   既定では、このテキストボックスはオンになっています。  
  
    -   このテキストボックスがオフの場合、移行されるデータは、ターゲットデータベースの既存のデータに追加されます。  
  
2.  **カスタム選択を使用する:**  
     このオプションを使用すると、ユーザーは現在の**select**ステートメントを変更できます (**select**ステートメントを使用すると、ターゲットデータベースに表示するデータをユーザーが選択できます)。  
  
    1.  既定では、このテキストボックスはオフになっています。  
  
    2.  このテキストボックスがオンになっている場合は、ユーザーが現在の**select**ステートメントを変更できます。  
  
可視化には、次の2つのボタンが表示されます。  
  
-   **適用:**[**適用**] をクリックして、変更された設定を適用します。  
  
-   **取り消し:** 変更が行われる前に設定を復元するには、[**キャンセル**] をクリックします。  
  
## <a name="see-also"></a>参照  
[Sybase データの SQL Server/SQL Azure への移行](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)  
  

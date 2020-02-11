---
title: データ移行の設定 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c2c903ef29ab1a103bc9aa4f7b061e83ee7f2a95
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67896369"
---
# <a name="data-migration-settings-mysqltosql"></a>データ移行の設定 (MySQLToSQL)
  
## <a name="data-migration-settings"></a>データの移行設定  
**データ移行設定**を使用すると、ユーザーはデータ移行のためのカスタムクエリを作成できます。  
  
-   このタブは、[プロジェクトの設定] で [**非表示**] に設定した場合に、[**拡張データ移行オプション**] が [**表示**] に設定され、非表示になるときに使用できます。 プロジェクトの移行設定の詳細については、「[プロジェクトの設定 (移行)](https://msdn.microsoft.com/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9) 」を参照してください。  
  
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
[MySQL データの SQL Server/SQL Azure への移行](https://msdn.microsoft.com/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  

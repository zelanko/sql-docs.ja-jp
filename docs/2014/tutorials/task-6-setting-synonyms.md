---
title: 'タスク 6: シノニムの設定 |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a6f4e870dca91e952fbeea95ef8f1198c64d8d6b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054277"
---
# <a name="task-6-setting-synonyms"></a>タスク 6: シノニムを設定する
  このタスクでは、 **Country**ドメインの2つのドメイン値 ( **USA**と**米国**) を、**米国**を先頭の値としてシノニムとして設定します。 **Country**ドメインの作成時に [**先頭の値を使用する**] オプションが選択されているため、 **country**ドメインの**米国**の値は**米国**として出力されます (米国は先頭の値になります)。 詳細については、「[ドメイン値の変更](https://msdn.microsoft.com/library/hh510408.aspx)」を参照してください。

1.  ドメインの一覧から [ **Country** ] を選択します。

2.  [**ドメイン値**] タブに切り替えます。

3.  ツールバーの [**新しいドメイン値の追加**] ボタンをクリックします。

4.  値に「 **USA** 」と入力し、 **enter**キーを押します。

5.  CTRL キーまたは SHIFT キーを使用して**米国**と**USA**を複数選択するには、選択した項目を右クリックし、[**シノニムとして設定**] をクリックします。 これらの値がグループ化されて、値の 1 つが先頭の値として指定され、その他の値がその値に置き換えられます。

     ![[シノニムとして設定] メニュー](../../2014/tutorials/media/et-settingsynonyms-01.jpg "[シノニムとして設定] メニュー")

6.  **米国**が先頭の値として設定されていることに注意してください。 USA を先頭の値にする場合は、USA を右クリックし、[先頭に**設定**] オプションを選択します。 このチュートリアルでは、**米国**を先頭の値として使用します。

     ![シノニムとしての米国と USA](../../2014/tutorials/media/et-settingsynonyms-02.jpg "シノニムとしての米国と USA")

## <a name="next-step"></a>次の手順
 [タスク 7: 複合ドメインを作成する](../../2014/tutorials/task-7-creating-a-composite-domain.md)



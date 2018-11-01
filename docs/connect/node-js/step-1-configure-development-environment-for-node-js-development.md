---
title: 'ステップ 1: Node.js 開発用に開発環境を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823177f8fef91dda8cf879f6be84ef6706224fad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600240"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>ステップ 1: Node.js 開発用に開発環境を構成する
SQL Server 用 Node.js ドライバーを使用してアプリケーションを開発するために、前提条件、開発環境を構成する必要があります。  ノード パッケージ マネージャー (npm) を使用して、面倒なモジュールをインストールする最も一般的な方法がダウンロードできるは面倒なモジュールに直接[Github](https://github.com/pekim/tedious)したい場合。  
  
Node.js ドライバーが SQL Server と Azure SQL Database での既定で有効になっている TDS プロトコルを使用することに注意してください。  追加の構成は必要ありません。  
  
## <a name="windows"></a>Windows  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
A. 移動して[Node.js](https://nodejs.org/en/download/)  
B. 適切な Windows インストーラーの msi リンクをクリックします。   
c. Node.js をインストールする msi をダウンロードしたら、実行します。  
  
2. **Cmd.exe を開きます**  
  
3. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> npm init  
```  
  
5. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **ターミナルを開く**  
  
2. **Node.js ランタイムをインストールします。**  
```  
>sudo apt-get install node  
```  
3. **Npm (ノード パッケージ マネージャー) をインストールします。**  
```  
> sudo apt-get install npm  
```  
4. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> sudo npm init  
```  
  
6. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Node.js ランタイムと npm パッケージ マネージャーをインストールします。**  
A. 移動して[Node.js](https://nodejs.org/en/download/)  
B. 該当する Mac OS インストーラー リンクをクリックします。  
c. Node.js をインストールする dmg をダウンロードしたら、実行します。  
  
2. **ターミナルを開く**  
  
3. **プロジェクト ディレクトリを作成**に移動します。    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **ノードのプロジェクトを作成します。**  プロジェクトの作成中に、既定値を保持するには、キーを押して、プロジェクトが作成されるまでを入力します。 この手順の最後に、プロジェクト ディレクトリに package.json ファイルを参照してください必要があります。  
```  
> npm init  
```  
  
5. **プロジェクトで面倒なモジュールをインストールします。**  これは、ドライバーが SQL Server との通信に使用する、TDS プロトコルの実装です。  
```  
> npm install tedious  
```  
  

// ==UserScript==
// @name         StarBreak:deadline // ==UserScript==
// @name         Aqurias
// @namespace    http://ryara.net/
// @version      0.1
// @author       tobbez
// @match        https://www.starbreak.com/*
// @match        https://*.starbreak.com/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    /*
     * Add one entry below for each of the sprite sheets you want to replace (and replace/remove the example one).
     * The format of the name is name.index, for example forest.0 or lab.1.
     * The URL is the URL to the replacement sprite sheet.
     */
    let replacementTextures = {
        'scboss.0': 'https://i.imgur.com/1Kk2z07.png',
        'scboss.1': 'https://i.imgur.com/df8rZum.png',
        'scboss.2': 'https://i.imgur.com/8bzqqWA.png',
        'cave.0': 'https://i.imgur.com/aBWlvLb.png',
        'cave.1': 'https://i.imgur.com/OZP2lU5.png',
        'cave.2': 'https://i.imgur.com/twf7Dz1.png',
        'cave-s.0': 'https://i.imgur.com/d6JWtfg.png',
        'ui.0': 'https://i.imgur.com/SfyPO4Z.png',
        'lab.0': 'https://i.imgur.com/jSZLSPn.png',
        'lab.1': 'https://i.imgur.com/guPDeBp.png',
        'lab.2': 'https://i.imgur.com/XaMoqdA.png',
        'hulk.0': 'https://i.imgur.com/ySwVPBl.png',
        'hulk.1': 'https://i.imgur.com/JbyZIsC.png',
        'hulk.2': 'https://i.imgur.com/YQKbxZ8.png',
        'dumb.2': 'https://i.imgur.com/HPZnhB8.png',
        'dumb.0': 'https://i.imgur.com/s6dtjqe.png',
        'dumb.1': 'https://i.imgur.com/J7LLv9R.png',
        'jungle.0': 'https://i.imgur.com/5JYHYs1.png',
        'jungle.1': 'https://i.imgur.com/bQbPUZa.png',
        'jungle.2': 'https://i.imgur.com/rXW6U3X.png',
        'jungles-0': 'https://i.imgur.com/3w2GUTE.png',
        'base.1': 'https://i.imgur.com/zm2KrVP.png',
        'base.0': 'https://i.imgur.com/BvvtGZx.png',
        'lobby.0': 'https://i.imgur.com/LegP5GD.png',
        'lobby.1': 'https://i.imgur.com/4Qxakxq.png',
        'home.0': 'https://i.imgur.com/uBr4m3D.png',
        'home.1': 'https://i.imgur.com/qIihT5z.png',


    };

    function onLoaded () {
        XDL.loadTexture = function (filename, doneCallback, userData) {
            let textureName = filename.split('.').slice(0,2).join('.').split('/')[1];
            let realFilename = filename;
            if (textureName in replacementTextures) {
                realFilename = replacementTextures[textureName];
            }
            var image = new Image();

            image.crossOrigin = "Anonymous";

            image.src = realFilename;
            image.onload = function() {
                var textureId = XDL.renderEngine.addTexture(image);
                Runtime.dynCall('vii', doneCallback, [textureId, userData]);
            };
            image.onerror = function() {
                console.error('error trying to load ' + filename + ', retrying');
                setTimeout(function() {
                    XDL.loadTexture(filename, doneCallback, userData);
                }, 1000);
            };
        };
    }

    function waitUntilLoaded () {
        if (typeof XDL == 'undefined') {
            setTimeout(waitUntilLoaded, 100);
            return;
        }
        onLoaded();
    }

    waitUntilLoaded();
})()
// @namespace    http://ryara.net/
// @version      0.1
// @author       tobbez
// @match        https://www.starbreak.com/*
// @match        https://*.starbreak.com/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    /*
     * Add one entry below for each of the sprite sheets you want to replace (and replace/remove the example one).
     * The format of the name is name.index, for example forest.0 or lab.1.
     * The URL is the URL to the replacement sprite sheet.
     */
    let replacementTextures = {
        'lobby.0': 'https://i.imgur.com/0g9kvc9.png',
        'base.1': 'https://i.imgur.com/8Pq3JGG.png',
        'hulk.0': 'https://i.imgur.com/1tiMHom.png',
        'hulk.1': 'https://i.imgur.com/9q4bk2j.png',
        'hulk.2': 'https://i.imgur.com/jZGraMn.png',
        'base.0':'https://i.imgur.com/2EBAXry.png',
        'lobby.1': 'https://i.imgur.com/GSmdCXG.png',
        'home.0': 'https://i.imgur.com/x7PTQIn.png',
        'home.1':'https://i.imgur.com/sCeAMYF.png',
        'jungle.0': 'https://i.imgur.com/jZrXhRv.png',
        'jungle.1': 'https://i.imgur.com/m2ICd82.png',
        'jungle.2': 'https://i.imgur.com/NQ4hQzV.png',
        'jungle-s.0': 'https://i.imgur.com/HGz2YF4.png',
        'dumb.0': 'https://i.imgur.com/toh48xA.png',
        'dumb.1': 'https://i.imgur.com/Pq8syNS.png',
        'dumb.2': 'https://i.imgur.com/jbftCsa.png',
        'dumb-s.0': 'https://i.imgur.com/vXCdykW.png',
         'lab.0': 'https://i.imgur.com/ZfIXNHX.png',
        'lab.1': 'https://i.imgur.com/ZJAiWRV.png',
        'lab.2': 'https://i.imgur.com/gnbZF5e.png',
        'title.0': 'https://i.imgur.com/iEcxaK5.png',
        'cave.0': 'https://i.imgur.com/wkKzbgr.png',
        'ui.0':'https://i.imgur.com/6NlTg52.png',
        'scboss.0':'https://i.imgur.com/KNsPpTy.png',
        'scboss.1':'https://i.imgur.com/l42qrXq.png',
        'scboss.2':'https://i.imgur.com/DeTjyem.png',
        'cave.0':'https://i.imgur.com/3CNXvUw.png',
        'cave.1':'https://i.imgur.com/LQUeVCV.png',
        'cave.2':'https://i.imgur.com/2pq7zJJ.png',
        'cave-s.0':'https://i.imgur.com/xW2W6Bq.png',
        'ice.0':'https://i.imgur.com/ncvCSWH.png',
        'ice.1':'https://i.imgur.com/Xv1PWcg.png',
        'ice.2':'https://i.imgur.com/1t4va6A.png',
        'ice.3':'https://i.imgur.com/0ep7TSW.png',
    };

    function onLoaded () {
        XDL.loadTexture = function (filename, doneCallback, userData) {
            let textureName = filename.split('.').slice(0,2).join('.').split('/')[1];
            let realFilename = filename;
            if (textureName in replacementTextures) {
                realFilename = replacementTextures[textureName];
            }
            var image = new Image();

            image.crossOrigin = "Anonymous";

            image.src = realFilename;
            image.onload = function() {
                var textureId = XDL.renderEngine.addTexture(image);
                Runtime.dynCall('vii', doneCallback, [textureId, userData]);
            };
            image.onerror = function() {
                console.error('error trying to load ' + filename + ', retrying');
                setTimeout(function() {
                    XDL.loadTexture(filename, doneCallback, userData);
                }, 1000);
            };
        };
    }

    function waitUntilLoaded () {
        if (typeof XDL == 'undefined') {
            setTimeout(waitUntilLoaded, 100);
            return;
        }
        onLoaded();
    }

    waitUntilLoaded();
})();

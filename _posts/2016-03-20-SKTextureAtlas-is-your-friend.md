---
layout: post
title: SKTextureAtlas is your friend
published: true
---

Have you been working with SpriteKit and had strange messages on the console like this one? 


```bash
CUICatalog: Invalid Request: requesting subtype without specifying idiom
```

Perhaps you are struggling with images in your texture atlas that just don't look right on the screen.
While scaling images for all of the possible resolutions you may want to support in your game is an
important topic, this may instead have to do with how you are creating your SKTextures and SKSpriteNodes.


As of the time of this post (03/20/2016, Xcode 7.2.1), it matters *how* you reference your images.

This post assumes you are using two things.

1. [Asset Catalogs](https://developer.apple.com/library/ios/recipes/xcode_help-image_catalog-1.0/chapters/Recipe.html)
2. Your images are included in a Sprite Atlas in the Asset Catalog.



Here are some examples that will get you some odd results.

**Creation by resource name**

Swift:

``` swift
let texture = SKTexture(imageNamed: "CoolHero")
```

Objective-C:

``` objc
SKTexture *texture = [SKTexture textureWithImageNamed:@"CoolHero"];
```



I recommend you try creating these from SKTextureAtlas.

**Creation from the Atlas**

Swift:

``` swift
let texture = SKTextureAtlas(named: "Sprites").textureNamed("CoolHero")
```

Objective-C


``` objc
SKTexture *texture = [[SKTextureAtlas atlasNamed:@"Sprites"] textureNamed:@"CoolHero"];
```


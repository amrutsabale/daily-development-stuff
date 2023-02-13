Ref: https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state

````
  animation: '$shine 2s infinite',
  '@keyframes shine': {
    '0%': { backgroundPosition: 'right' },
  },
````

if we want stop with condtion
````
 animationPlayState: ({ hasCondition }: makeStylesProps) =>
        hasCondition ? 'paused' : 'running',
````

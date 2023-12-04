lines: read.lines relative "input.txt"
lines: @[repeat "." size first lines] ++ lines ++ @[repeat "." size first lines]

print sum flatten map 1..(size lines)-2 'i [
    lines\[i] | match.bounds {/\*/}
              | map 'mtch [
                    gears: (i-1)..(i+1) | map 'x [get match.full lines\[x] {/\d+/} 'matches]
                                        | flatten.once
                                        | select 'm [subset? @m\1 @ ((first mtch) - size m\0)..((last mtch) + size m\0)]
                                        | map 'z [to :integer first z]

                    (2 = size gears)? -> product gears -> 0
              ]
]
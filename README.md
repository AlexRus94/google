//
//  SwiftRobotControlCenter.swift
//  MyRobot
//
//  Created by Ivan Vasilevich on 10/4/14.
//  Copyright (c) 2014 Ivan Besarab. All rights reserved.
//

import UIKit
//  All robot commands can be founded in GameViewController.h
class SwiftRobotControlCenter: RobotControlCenter {
    
    //  Level name setup
    override func viewDidLoad() {
        levelName = "L2C" //  Level name
        super.viewDidLoad()
    }
    
    override func run() {
        for _ in 0...13 {
            findPeak()
            moveUp()
            uTurn()
            moveDown()
            
        }
    }
    
    func findPeak() {
        while frontIsClear {
            move()
        }
        if frontIsBlocked {
            turnRight()
        }
        
        
        
    }
    
    func moveUp () {
        while leftIsBlocked {
            move()
            if leftIsClear {
                uTurn()
            }
            if frontIsBlocked {
                break
                
            }
        }
    }
    func moveDown () {
        while frontIsClear {
            move()
            
        }
        if frontIsBlocked {
            turnRight()
            findPeak()
        }
        
    }
    
    
    func uTurn () {
        turnLeft()
        move()
        turnLeft()
        if frontIsClear {
            moveDown()
        }
        
    }
    func turnLeft () {
        turnRight()
        turnRight()
        turnRight()
    }
}
